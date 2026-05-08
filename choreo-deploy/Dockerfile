# ============================================================
# n8n on Choreo (WSO2 Developer Platform)
# ------------------------------------------------------------
# Choreo enforces non-root container execution with UID 10000-20000.
# The official n8n image runs as 'node' (UID 1000).
# We remap the existing 'node' user to UID/GID 10001 so all PATH
# and entrypoint wiring from the base image is preserved.
# ============================================================
FROM n8nio/n8n:latest

USER root

# Remap the existing 'node' user/group from UID/GID 1000 → 10001
# using sed (no external tools needed)
RUN sed -i "s/^node:x:1000:1000:/node:x:10001:10001:/" /etc/passwd \
    && sed -i "s/^node:x:1000:/node:x:10001:/" /etc/group \
    && chown -R 10001:10001 /home/node

USER 10001

EXPOSE 5678
