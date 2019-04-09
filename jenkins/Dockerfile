FROM jenkins/jenkins:lts

FROM jenkins/jenkins:lts
# if we want to install via apt
USER root
RUN apt-get update && apt-get install -y maven


# drop back to the regular jenkins user - good practice
USER jenkins

# install jenkins plugins
COPY plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/plugins.txt

ENV JAVA_OPTS -Dorg.eclipse.jetty.server.Request.maxFormContentSize=100000000 \
 			  -Dorg.apache.commons.jelly.tags.fmt.timeZone=Australia/Sydney \
 			  -Dhudson.diyChunking=false \
 			  -Dhudson.security.csrf.GlobalCrumbIssuerConfiguration=true \
			  -Djenkins.CLI.disabled=true \
 			  -Djenkins.install.runSetupWizard=false

# copy scripts and ressource files
