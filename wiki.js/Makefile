.PHONY=all clean clean-all status run
.PHONY+=docker-compose-up postgresql python3-venv run-etl

# Force make to run targets sequentially
.NOTPARALLEL:

# Directory containing this makefile. Includes trailing slash
MAKEFILE_PATH=$(dir $(realpath $(firstword $(MAKEFILE_LIST))))

# Set default shell as bash
# This is necessary because we use "source" below
SHELL:=/bin/bash

# Path to the virtual environment
VENV_DIR=$(MAKEFILE_PATH).env

# Specify which python version to use to make a virtual environment
VENV_PYTHON=python3


all: run

clean:
	$(info Clean)
	./run --docker-compose-down

clean-all:
	$(info Clean All)
	./run --clean-all
	echo "Remove Postgresql database files"
	cd ./postgresql && sudo rm -rf ./pg_data

status:
	$(info Show docker status)
	./run --status

docker-compose-up:
	$(info Running docker-compose up)
	./run --docker-compose-up

run: docker-compose-up
	$(info Opening Browser to Wiki)
	xdg-open http://localhost:80
