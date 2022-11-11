FROM python:3.11

# Install missing 'ps' command that some VS Code extensions depend on:
RUN apt update && \
    apt install -y procps

RUN groupadd -g 1000 -r developer && \
    useradd -u 1000 -r -g developer -m -s $(which bash) developer
# Option '-m' to create home directory (see https://askubuntu.com/a/393470)
# Option '-s' to set  shell for this user (see comment in https://askubuntu.com/a/393470)
# Option '-r' creates a system user which does not expire 
#             (see https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/)

WORKDIR /app
COPY requirements.txt ./
RUN pip install -r ./requirements.txt

# Install dotnet-outdated (see https://github.com/dotnet-outdated/dotnet-outdated)
# RUN runuser -l developer -c "dotnet tool install --global dotnet-outdated-tool"
# runuser installs it as if the non-root user was installing it. This makes 
# it available to that non-root user


# ENV PATH "$PATH:/home/developer/.dotnet/tools"
USER developer
