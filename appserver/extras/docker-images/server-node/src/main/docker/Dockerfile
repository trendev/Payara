#
#    DO NOT ALTER OR REMOVE COPYRIGHT NOTICES OR THIS HEADER.
#
#    Copyright (c) 2023 Payara Foundation and/or its affiliates. All rights reserved.
#
#    The contents of this file are subject to the terms of either the GNU
#    General Public License Version 2 only ("GPL") or the Common Development
#    and Distribution License("CDDL") (collectively, the "License").  You
#    may not use this file except in compliance with the License.  You can
#    obtain a copy of the License at
#    https://github.com/payara/Payara/blob/master/LICENSE.txt
#    See the License for the specific
#    language governing permissions and limitations under the License.
#
#    When distributing the software, include this License Header Notice in each
#    file and include the License file at glassfish/legal/LICENSE.txt.
#
#    GPL Classpath Exception:
#    The Payara Foundation designates this particular file as subject to the "Classpath"
#    exception as provided by the Payara Foundation in the GPL Version 2 section of the License
#    file that accompanied this code.
#
#    Modifications:
#    If applicable, add the following below the License Header, with the fields
#    enclosed by brackets [] replaced by your own identifying information:
#    "Portions Copyright [year] [name of copyright owner]"
#
#    Contributor(s):
#    If you wish your version of this file to be governed by only the CDDL or
#    only the GPL Version 2, indicate your decision by adding "[Contributor]
#    elects to include this software in this distribution under the [CDDL or GPL
#    Version 2] license."  If you don't indicate a single choice of license, a
#    recipient has the option to distribute your version of this file under
#    either the CDDL, the GPL Version 2 or to extend the choice of license to
#    its licensees as provided above.  However, if you add GPL Version 2 code
#    and therefore, elected the GPL Version 2 license, then the option applies
#    only if the new code is made subject to such option by the copyright
#    holder.

FROM payara/basic:@docker.payara.tag@

ENV PAYARA_DAS_HOST="localhost" \
    PAYARA_DAS_PORT="4848" \
    PAYARA_NODE_NAME="" \
    PAYARA_CONFIG_NAME="" \
    PAYARA_INSTANCE_NAME="" \
    DOCKER_CONTAINER_IP=""
ENV PAYARA_PASSWORD_FILE_DIR=${HOME_DIR}/passwords
ENV PAYARA_PASSWORD_FILE=${PAYARA_PASSWORD_FILE_DIR}/passwordfile.txt

# Create and set the Payara user and working directory owned by the new user
RUN true \
    && mkdir -p ${PAYARA_PASSWORD_FILE_DIR} \
    && true

COPY --chown=payara:payara maven/artifacts/@docker.payara.rootDirectoryName@ ${PAYARA_DIR}
COPY --chown=payara:payara maven/bin/* ${SCRIPT_DIR}

ENTRYPOINT "${SCRIPT_DIR}/entrypoint.sh"
