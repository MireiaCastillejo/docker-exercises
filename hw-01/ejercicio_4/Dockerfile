FROM nginx:1.19.3-alpine

HEALTHCHECK --interval=45s --timeout=5s --start-period=15s --retries=2 \
  CMD curl --fail http://localhost || exit 1
