FROM library/node:lts-bookworm-slim

ARG DEBIAN_FRONTEND=noninteractive
RUN apt update \
    && apt install -y --no-install-recommends sudo git openssh-client \
    && apt autoremove -y \
    && rm -rf /var/lib/apt/lists/* \
    && echo "node ALL=(ALL) NOPASSWD: ALL" >/etc/sudoers.d/node \
    && chmod 0440 /etc/sudoers.d/node

COPY .ssh /home/node/.ssh
RUN chown -R node:node /home/node/.ssh \
    && chmod 0600 /home/node/.ssh/id_ed25519 \
    && chmod 0644 /home/node/.ssh/id_ed25519.pub

RUN yarn set version berry
