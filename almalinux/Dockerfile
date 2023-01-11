FROM docker.io/almalinux/8-base

RUN set -eux ; \
    # Create dirs
    mkdir /alertmanager ; \
    mkdir /usr/local/etc/alertmanager ; \
    
    # Create user and set permissions
    useradd -d /alertmanager -M alertmanager ; \

    chown alertmanager:alertmanager  /alertmanager ;  \
    chown alertmanager:alertmanager /usr/local/etc/alertmanager ; \

    # Get alertmanager
    url='https://github.com/prometheus/alertmanager/releases/download/v0.25.0/alertmanager-0.25.0.linux-amd64.tar.gz' ; \
    curl -fsSLo /tmp/alertmanager.tar.gz $url ; \
    mkdir /tmp/alertmanager && \
        tar -C /tmp/alertmanager --strip-components 1 -xf /tmp/alertmanager.tar.gz ; \
    chown -R alertmanager:alertmanager /tmp/alertmanager ; \
    rm /tmp/alertmanager.tar.gz ; \

    # Move alertmanager files to dirs
    mv /tmp/alertmanager/{alertmanager,amtool} /usr/local/bin ; \
    mv /tmp/alertmanager/{alertmanager.yml,LICENSE,NOTICE} /usr/local/etc/alertmanager ; 

    WORKDIR "/alertmanager"

    VOLUME ["/alertmanager"]

    EXPOSE 9093

    USER alertmanager

    ENTRYPOINT ["/usr/local/bin/alertmanager"]

    CMD ["--config.file=/usr/local/etc/alertmanager/alertmanager.yml", \
         "--storage.path=/alertmanager"]
