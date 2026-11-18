# Issue

**Title:** Objective function supports caching

## Description

Substantial performance benefits gained especially with function runs with high population size and max iteration arguments


`
  import torch
  import numpy as np
  import pandas as pd
  from scipy.stats import norm
  import statsmodels.api as sm
  import matplotlib.pyplot as plt
  from datetime import datetime
  import requests
  from io import BytesIO
  import time
  from sko.GA import GA
  import warnings
  warnings.filterwarnings("ignore")
# Dataset
  
  austourists_data = [
      30.05251300, 19.14849600, 25.31769200, 27.59143700,
      32.07645600, 23.48796100, 28.47594000, 35.12375300,
      36.83848500, 25.00701700, 30.72223000, 28.69375900,
      36.64098600, 23.82460900, 29.31168300, 31.77030900,
      35.17787700, 19.77524400, 29.60175000, 34.53884200,
      41.27359900, 26.65586200, 28.27985900, 35.19115300,
      42.20566386, 24.64917133, 32.66733514, 37.25735401,
      45.24246027, 29.35048127, 36.34420728, 41.78208136,
      49.27659843, 31.27540139, 37.85062549, 38.83704413,
      51.23690034, 31.83855162, 41.32342126, 42.79900337,
      55.70835836, 33.40714492, 42.31663797, 45.15712257,
      59.57607996, 34.83733016, 44.84168072, 46.97124960,
      60.01903094, 38.37117851, 46.97586413, 50.73379646,
      61.64687319, 39.29956937, 52.67120908, 54.33231689,
      66.83435838, 40.87118847, 51.82853579, 57.49190993,
      65.25146985, 43.06120822, 54.76075713, 59.83447494,
      73.25702747, 47.69662373, 61.09776802, 66.05576122,
      30.05251300, 19.14849600, 25.31769200, 27.59143700,
      32.07645600, 23.48796100, 28.47594000, 35.12375300,
      36.83848500, 25.00701700, 30.72223000, 28.69375900,
      36.64098600, 23.82460900, 29.31168300, 31.77030900,
      35.17787700, 19.77524400, 29.60175000, 34.53884200,
      41.27359900, 26.65586200, 28.27985900, 35.19115300,
      42.20566386, 24.64917133, 32.66733514, 37.25735401,
      45.24246027, 29.35048127, 36.34420728, 41.78208136,
      49.27659843, 31.27540139, 37.85062549, 38.83704413,
      51.23690034, 31.83855162, 41.32342126, 42.79900337,
      55.70835836, 33.40714492, 42.31663797, 45.15712257,
      59.57607996, 34.83733016, 44.84168072, 46.97124960,
      60.01903094, 38.37117851, 46.97586413, 50.73379646,
      61.64687319, 39.29956937, 52.67120908, 54.33231689,
      66.83435838, 40.87118847, 51.82853579, 57.49190993,
      65.25146985, 43.06120822, 54.76075713, 59.83447494,
      73.25702747, 47.69662373, 61.09776802, 66.05576122,
  ]
  austourists = pd.Series(austourists_data)

  
  
  def arima(X):
      X = [int(x) for x in X]
  
      p, d, q, P, D, Q = X
      s = 12
      order = [p, d , q]
  
      seasonal_order = [P, D, Q, s]
  
      limit = d + D*s + max(3*q + 1, 3*Q*s + 1, p, P*s) + 1
  
      if len(austourists) < limit:
          raise Exception("Too little data")
  
      mod = sm.tsa.statespace.SARIMAX(austourists, 
                                      order=order, 
                                      seasonal_order = seasonal_order,
                                      enforce_stationarity=False,
                                      enforce_invertibility=False
                                      )
      res = mod.fit(disp=False)
  
      return res.aic
  
  
  
  ga = GA(func=arima, n_dim=6, size_pop=50, max_iter=2, lb=[0,0,0,0,0,0], ub=[6,4,6,2,1,2], precision=1)
  arima.is_parallel = False
  arima.is_cached = True
  
  device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
  
  ga.to(device=device)
  
  
  ga = GA(func=arima, n_dim=6, size_pop=50, max_iter=2, lb=[0,0,0,0,0,0], ub=[6,4,6,2,1,2], precision=1)
  
  
  
  time_start = time.time()
  best_x, best_y = ga.run()
  print('time cost:', time.time() - time_start, ' seconds')
`


Output:

time cost: 230.0302619934082  seconds
time cost: 1253.6365308761597  seconds


I have tested it caching with parallel process enabled as well, there I have observed similar benefits of caching

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5538c9774cc9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.