FROM czar8a/weblogic:datasource


# Maintainer
# ----------
MAINTAINER Cesar Ochoa <czar8a@gmail.com>

# Environment variables required for this build
# ---------------------------------------------
ENV  JAVA_HOME=/usr/local/jdk1.7.0_80 \
	PATH=$JAVA_HOME/bin:$PATH \
	MW_HOME=/u01/app/oracle/middleware \
	WLS_HOME=$MW_HOME/wls_12.1.1 \
	USER_MEM_ARGS="-Xms32m -Xmx200m -XX:MaxPermSize=350m"


USER oracle

WORKDIR /u01/oracle

# Define default command to start bash.
CMD ["/u01/app/oracle/middleware/user_projects/domains/SnapDomain/startWebLogic.sh"]
#CMD ["bash"]