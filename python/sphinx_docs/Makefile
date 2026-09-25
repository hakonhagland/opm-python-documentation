.PHONY: docs view-docs

CURRENT_BRANCH := $(shell git rev-parse --abbrev-ref HEAD)
GIT_ROOT := $(shell git rev-parse --show-toplevel)

# Build the documentation locally for the current branch
# NOTE: You need to commit your changes before running this command
docs:
	sphinx-versioned -m ${CURRENT_BRANCH} -b ${CURRENT_BRANCH} --git-root ../../

# opmdoc-view-doc opens the page with the platform's own opener (xdg-open, open or start)
view-docs:
	@opmdoc-view-doc --branch=$(CURRENT_BRANCH)

test:
	pytest tests/

coverage:
	coverage run -m pytest tests
	coverage report -m
