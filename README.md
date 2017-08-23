# NGINX On OpenShift

OpenShift imposes a security context by default which prevents running containers as root.

Not only that, but it randomly selects a high-range UID, and GID 0. This essentially makes
the FS read-only.

In the case of NGinx, it also prevents us from starting as root, which prevents us from
listening on port 80. And running as the nginx user isn't possible either because of mismatchin
UIDs.

A couple chmods in the right place, and listening on port 8080 solves the problem.
