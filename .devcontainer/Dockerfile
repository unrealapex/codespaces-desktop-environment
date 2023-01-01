FROM mcr.microsoft.com/devcontainers/base:bullseye
USER root

COPY library-scripts/desktop-lite-debian.sh /tmp/library-scripts/
RUN apt-get update && bash /tmp/library-scripts/desktop-lite-debian.sh

# install brave
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://b
rave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=
amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /et
c/apt/sources.list.d/brave-browser-release.list
sudo apt update
sudo apt install brave-browser

# vnc environment variables
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
