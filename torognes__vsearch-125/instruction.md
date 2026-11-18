# Issue

**Title:** Fix example in man page

## Description

Hi,

Just noticed this little thing.

I noticed it while I was packaging vsearch for the GNU Guix package manager - if you have any comments on how I packaged it please do speak up. The mailing list where guix patches are submitted  seems to be down at the moment, but when it is back up my patch will be sent through.
http://lists.gnu.org/archive/html/guix-devel/2015-09/threads.html

Here's the guix patch.

``` scheme
+(define-public vsearch
+  (package
+    (name "vsearch")
+    (version "1.4.1")
+    (source
+     (origin
+       (method url-fetch)
+       (uri (string-append
+             "https://github.com/torognes/vsearch/archive/v"
+             version ".tar.gz"))
+       (file-name (string-append name "-" version ".tar.gz"))
+       (sha256
+        (base32
+         "0b1359wbzgb2cm04h7dq05v80vik88hnsv298xxd1q1f2q4ydni7"))
+       (modules '((guix build utils)))
+       (snippet
+        '(begin
+           ;; Remove bundled cityhash
+           (substitute* "src/Makefile.am"
+             (((string-append "^AM_CXXFLAGS=-I\\$\\{srcdir\\}/cityhash"
+                              " -O3 -mtune=native -Wall -Wsign-compare"))
+              (string-append "AM_CXXFLAGS=-lcityhash"
+                             " -O3 -mtune=native -Wall -Wsign-compare"))
+             (("^__top_builddir__bin_vsearch_SOURCES = cityhash/city.h \\\\")
+              "__top_builddir__bin_vsearch_SOURCES = \\")
+             (("^cityhash/config.h \\\\") "\\")
+             (("^cityhash/city.cc \\\\") "\\"))
+           (substitute* "src/vsearch.h"
+             (("^\\#include \"cityhash/city.h\"")
+              "#include <city.h>"))
+           (delete-file-recursively "src/cityhash")
+           #t))))
+    (build-system gnu-build-system)
+    (arguments
+     `(#:phases
+       (modify-phases %standard-phases
+         (add-before 'configure 'autogen
+                     (lambda _ (zero? (system* "autoreconf" "-vif")))))))
+    (inputs
+     `(("zlib" ,zlib)
+       ("bzip2" ,bzip2)
+       ("cityhash" ,cityhash)))
+    (native-inputs
+     `(("autoconf" ,autoconf)
+       ("automake" ,automake)))
+    (synopsis "Sequence search tools for metagenomics")
+    (description
+     "VSEARCH supports DNA sequence searching, clustering, chimera detection,
+dereplication, pairwise alignment, shuffling, subsampling, sorting and
+masking.  The tool takes advantage of parallelism in the form of SIMD
+vectorization as well as multiple threads to perform accurate alignments at
+high speed.  VSEARCH uses an optimal global aligner (full dynamic programming
+Needleman-Wunsch).")
+    (home-page "https://github.com/torognes/vsearch")
+    ;; dual licensed, plus some public domain source
+    (license (list license:gpl3 license:bsd-2 license:public-domain))))
```

Thanks,
ben

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f1e5c7e93a0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.