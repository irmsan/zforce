FROM s390x/bookworm-slim:latest 

ENV BUILD_DEPS='libica-utils openssl libssl-dev openssl-ibmca time s390-tools'

RUN set -x \
&&  apt-get update \
&&  apt-get install -y $BUILD_DEPS --no-install-recommends \
&&  rm -rf /var/lib/apt/lists/* \
&&  apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false

RUN set -x \
&&  tee -a /etc/ssl/openssl.cnf < /usr/share/doc/openssl-ibmca/examples/openssl.cnf.sample\
&&  sed -i -r 's/openssl_conf = default_conf/openssl_conf = openssl_def/' /etc/ssl/openssl.cnf
