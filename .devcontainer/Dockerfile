FROM mcr.microsoft.com/devcontainers/base:bullseye
USER root

COPY library-scripts/desktop-lite-debian.sh /tmp/library-scripts/
RUN apt-get update && bash /tmp/library-scripts/desktop-lite-debian.sh

# install google chrome
RUN wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb \
&& sudo apt -y install ./google-chrome*.deb \
&& sudo apt-get -y install -f


ENV DBUS_SESSION_BUS_ADDRESS="autolaunch:" \
    VNC_RESOLUTION="1280x720x32" \
    VNC_DPI="96" \
    VNC_PORT="5901" \
    NOVNC_PORT="6080" \
    DISPLAY=":1" \
    LANG="en_US.UTF-8" \
    LANGUAGE="en_US.UTF-8"
    
    
ENTRYPOINT ["/usr/local/share/desktop-init.sh"]
CMD ["sleep", "infinity"]
