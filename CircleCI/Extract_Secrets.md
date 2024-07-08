CircleCI:
version: 2.1

workflows:
  build:
    jobs:
      - build:
          context:
            - my-context

jobs:
  build:
    docker: 
      - image: cimg/base:stable
    steps:
      - run:
          name: whoami
          command: whoami
      - run:
          name: env variables
          command:  env | base64 
