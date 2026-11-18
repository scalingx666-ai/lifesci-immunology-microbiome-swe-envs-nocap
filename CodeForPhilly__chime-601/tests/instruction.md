# Issue

**Title:** Deploy CHIME 1.1.5

## Description

Actions to deploy v1.1.5:
```diff
diff -u -N /tmp/LIVE-311739531/apps.v1.Deployment.chime.chime /tmp/MERGED-782875758/apps.v1.Deployment.chime.chime
--- /tmp/LIVE-311739531/apps.v1.Deployment.chime.chime	2020-05-07 15:10:57.230600990 +0000
+++ /tmp/MERGED-782875758/apps.v1.Deployment.chime.chime	2020-05-07 15:10:57.282600957 +0000
@@ -9,12 +9,12 @@
     kubernetes.io/change-cause: kubectl set image deployment/chime chime=docker.pkg.github.com/codeforphilly/chime/penn-chime:1.0.0
       --namespace=chime --record=true
   creationTimestamp: "2020-03-17T22:40:47Z"
-  generation: 26
+  generation: 27
   labels:
     app: chime
   name: chime
   namespace: chime
-  resourceVersion: "18637392"
+  resourceVersion: "21011848"
   selfLink: /apis/apps/v1/namespaces/chime/deployments/chime
   uid: 0ee5c93a-5e1b-43ab-a510-60d8c4127995
 spec:
@@ -36,7 +36,7 @@
         app: chime
     spec:
       containers:
-      - image: docker.pkg.github.com/codeforphilly/chime/penn-chime:1.1.4
+      - image: docker.pkg.github.com/codeforphilly/chime/penn-chime:1.1.5
         imagePullPolicy: Always
         name: chime
         ports:
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `05fbf4845b19`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.