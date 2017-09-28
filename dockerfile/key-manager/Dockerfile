# ------------------------------------------------------------------------
#
# Copyright 2017 WSO2, Inc. (http://wso2.com)
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License
#
# ------------------------------------------------------------------------

FROM ubuntu:16.04
MAINTAINER dev@wso2.org

ARG PRODUCT_NAME=wso2is
ARG PRODUCT_VERSION=5.3.0
ARG JDK_TARBALL=jdk-8u144-linux-x64.tar.gz
ARG JDK_VERSION=jdk1.0.0_144

ENV PRODUCT_NAME=${PRODUCT_NAME} \
    PRODUCT_VERSION=${PRODUCT_VERSION} \
    JDK_TARBALL=${JDK_TARBALL} \
    JDK_VERSION=${JDK_VERSION}
    

WORKDIR /opt

COPY ${PRODUCT_NAME}-${PRODUCT_VERSION}.zip /opt
COPY ${JDK_TARBALL} /opt

ENV JAVA_HOME /opt/${JDK_VERSION}

# TODO: set proxy ports as needed

RUN apt-get update && \
    apt-get install -y --no-install-recommends --no-install-suggests \
      zip unzip net-tools && \
    unzip /opt/${PRODUCT_NAME}-${PRODUCT_VERSION}.zip && \
    tar zxvf  /opt/${JDK_TARBALL} && \
    rm -rf ${JDK_TARBALL} ${PRODUCT_NAME}-${PRODUCT_VERSION}.zip

USER root
# EXPOSE 9443 9763

WORKDIR /opt/${PRODUCT_NAME}-${PRODUCT_VERSION}

# ENTRYPOINT ["bin/wso2server.sh"]
# export JAVA_HOME=${JAVA_HOME}
CMD export JAVA_HOME=${JAVA_HOME} \
    && bin/wso2server.sh
