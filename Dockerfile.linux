# escape=`
FROM lacledeslan/gamesvr-hldms

HEALTHCHECK NONE

ARG BUILDNODE=unspecified
ARG SOURCE_COMMIT=unspecified

LABEL com.lacledeslan.build-node=$BUILDNODE `
      org.label-schema.schema-version="1.0" `
      org.label-schema.url="https://github.com/LacledesLAN/README.1ST" `
      org.label-schema.vcs-ref=$SOURCE_COMMIT `
      org.label-schema.vendor="Laclede's LAN" `
      org.label-schema.description="LL Half-Life Deathmatch Source Dedicated Freeplay Server" `
      org.label-schema.vcs-url="https://github.com/LacledesLAN/gamesvr-hldms-freeplay"

COPY --chown=HLDMS:root ./sourcemod.linux /app/hl1mp/

COPY --chown=HLDMS:root ./sourcemod-configs /app/hl1mp/

COPY --chown=HLDMS:root ./dist /app/

COPY --chown=HLDMS:root ./ll-tests/*.sh /app/ll-tests

# UPDATE USERNAME & ensure permissions
RUN usermod -l HLDMSFreeplay HLDMS &&`
    chmod +x /app/ll-tests/*.sh &&`
    mkdir -p /app/hl1mp/logs;

USER HLDMSFreeplay

WORKDIR /app

CMD ["/bin/bash"]

ONBUILD USER root
