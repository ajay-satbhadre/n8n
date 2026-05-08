# ============================================================
# n8n on Choreo (WSO2 Developer Platform)
# ------------------------------------------------------------
# Choreo enforces non-root container execution.
# The official n8n image runs as 'node' (UID 1000).
# This Dockerfile re-maps ownership to UID 10001 (10000-20000 range).
# ============================================================
FROM n8nio/n8n:latest

USER root

# Create a dedicated group + user with UID/GID 10001
RUN addgroup -S -g 10001 n8ngroup \
    && adduser  -S -u 10001 -G n8ngroup n8nuser \
    && mkdir -p /home/n8nuser/.n8n \
    && chown -R 10001:10001 /home/n8nuser

# Tell n8n where to store its data
ENV HOME=/home/n8nuser
ENV N8N_USER_FOLDER=/home/n8nuser/.n8n

# Drop privileges — USER directive value must be 10000–20000
USER 10001

EXPOSE 5678

CMD ["n8n", "start"]
