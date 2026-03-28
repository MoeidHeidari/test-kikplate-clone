> **Scaffolded from [nestjs-starter](https://github.com/MoeidHeidari/sudoku-challenge)** via [kikplate](https://github.com/kickplate/kikplate)

# sudoku-challenge


A standard [Sudoku](https://en.wikipedia.org/wiki/Sudoku "Sudoku") contains 81 cells, in a 9×9 grid, and has 9 boxes, each box being the intersection of the first, middle, or last 3 rows, and the first, middle, or last 3 columns. Each cell may contain a number from one to nine, and each number can only occur once in each row, column, and box. A Sudoku starts with some cells containing numbers (*clues*), and the goal is to solve the remaining cells. Proper Sudokus have one solution. Players and investigators use a wide range of computer algorithms to solve Sudokus, study their properties, and make new puzzles, including Sudokus with interesting symmetries and other properties.

## Prerequisites:

NPM 14.X

Docker

docker-compose

helm -for production

skaffold -for production

minikube (or any other kubernetes cluster) -for production

---

## Clone

```bash
git clone https://gitlab.com/Moeidtopcoder/sudoku-challenge.git

cd sudoku-challenge
```

---

## Hierarchy

```bash
├── k8s
│   └── templates
│       └── tests
├── scripts
├── src
│   ├── application
│   │   ├── controllers
│   │   └── dtos
│   ├── domain
│   │   ├── decorators
│   │   ├── entities
│   │   ├── enums
│   │   │   └── httpResponse
│   │   ├── exceptions
│   │   ├── guards
│   │   ├── helpers
│   │   ├── interceptors
│   │   ├── interfaces
│   │   ├── modules
│   │   │   └── common
│   │   ├── pipes
│   │   └── services
│   │       └── common
│   └── infrastructure
│       ├── config
│       └── modules
│           └── common
└── __test__
    ├── controllers
    ├── e2e
    ├── factories
    └── service
```

---

## Instllation

```bash
cd scripts
bash start.h {argument}
```

Arguments: 

```bash
bash start.h -h

-h, --help              Print this help and exit
-build_docker           Build the docker image called "sudoku:latest"
-build_and_run_docker   Build the docker image and run on local machine
-stop_docker            Stop running docker container named "sudoku"
-run_app                Run application with npm in usual way for development
-run_test               Run npm test
-run_lint               Run npm lint
-generate_doc           Generate the code documentation
-deploy_on_kubernetes   you need to have a kubernetes cluster already up and running on the machine.
```

---

### Run without script

```bash
npm install
npm start
```

---

### Run the tests

```bash
npm test
```

---

### linting

```bash
npm run lint
```

---

### generate documentation

```bash
npm run doc
```

running on 

http://localhost:7000

---

### Build docker image

```bash
docker build . -t {image-name}
```

----

### .env

```bash
NODE_ENV={production|development}
NODE_PORT={port-number}
DIMENSION={dimension}
```

---

### Run in Browser

http://localhost:{port-number}/api/v1/sudoku
![](/images/sudoku-endpoint.png)

----

### API documentation

http://localhost:{port-number}/api

![](/images/swagger.png)

---

### Health check

http://localhost:{port-number}/health

![](/images/liveness.png)

---

### Deploy to kubernetes

through Makefile

```bash
make
```

through config files

```bash
cd k8s/configFiles

  kubectl apply -f sudoku-namespace.yaml,sudoku-configmap.yaml,sudoku-deployment.yaml,sudoku-service.yaml
```

![](/images/kubernetes.png)

### Prometheus metrics

http://localhost:{port-number}/metrics
