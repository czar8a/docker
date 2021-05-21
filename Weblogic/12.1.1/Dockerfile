FROM primetoninc/jdk:1.7
#FROM frolvlad/alpine-openjdk7

# Maintainer
# ----------
MAINTAINER Cesar Ochoa <czar8a@gmail.com>

# Environment variables required for this build
# ---------------------------------------------
ENV ORACLE_HOME=/u01/oracle \
    USER_MEM_ARGS="-Djava.security.egd=file:/dev/./urandom" \
    PATH=$PATH:/usr/java/default/bin:/u01/oracle/oracle_common/common/bin

# Setup required packages, filesystem, and oracle user.
# Install and configure Oracle JDK
# Adjust file permissions, go to /u01 as user 'oracle' to proceed with WLS installation
# ------------------------------------------------------------
RUN mkdir -p /u01 && \
    chmod a+xr /u01 && \
    useradd -b /u01 -d /u01/oracle -m -s /bin/bash oracle
	
RUN mkdir -p /usr/local/jdk1.7.0_80/jre/lib/endorsed && \
    chmod 777 /usr/local/jdk1.7.0_80/jre/lib/endorsed

ENV FMW_PKG=wls1211_generic.jar

# Copy packages and files
# -----------------------
COPY $FMW_PKG install.file oraInst.loc /u01/
RUN  chown oracle:oracle -R /u01

USER oracle
#RUN $JAVA_HOME/bin/java -jar /u01/$FMW_PKG -ignoreSysPrereqs -novalidation -silent -responseFile /u01/install.file -invPtrLoc /u01/oraInst.loc -jreLoc $JAVA_HOME ORACLE_HOME=$ORACLE_HOME INSTALL_TYPE="WebLogic Server" && \
 #   rm /u01/$FMW_PKG /u01/oraInst.loc /u01/install.file

WORKDIR $ORACLE_HOME

# Define default command to start bash.
CMD ["bash"]
