# syntax=docker/dockerfile:1.4
FROM --platform=linux/amd64 kong:latest

# Set environment variables first
ENV KONG_DATABASE="off" \
    KONG_DECLARATIVE_CONFIG="/usr/local/kong/declarative/kong.yml" \
    KONG_PROXY_ACCESS_LOG="/dev/stdout" \
    KONG_ADMIN_ACCESS_LOG="/dev/stdout" \
    KONG_PROXY_ERROR_LOG="/dev/stderr" \
    KONG_ADMIN_ERROR_LOG="/dev/stderr" \
    KONG_ADMIN_LISTEN="0.0.0.0:8001, 0.0.0.0:8444 ssl" \
    KONG_PROXY_LISTEN="0.0.0.0:8000, 0.0.0.0:8443 ssl" \
    KONG_LOG_LEVEL="debug" \
    KONG_PLUGINS="bundled,request-termination,custom-auth" \
    KONG_LUA_PACKAGE_PATH="/usr/local/share/lua/5.1/?.lua;;" \
    KONG_DECLARATIVE_CONFIG_STRING="{}" \
    KONG_NGINX_WORKER_PROCESSES="1" \
    KONG_NGINX_USER="kong kong" \
    KONG_NGINX_DAEMON="off"

# Copy files directly (Kong will create directories as needed)
COPY --chown=kong:kong custom-plugins/custom-auth/handler.lua /usr/local/share/lua/5.1/kong/plugins/custom-auth/
COPY --chown=kong:kong custom-plugins/custom-auth/schema.lua /usr/local/share/lua/5.1/kong/plugins/custom-auth/
COPY --chown=kong:kong config/kong.yml /usr/local/kong/declarative/

EXPOSE 8000 8443 8001 8444

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["kong", "docker-start"]