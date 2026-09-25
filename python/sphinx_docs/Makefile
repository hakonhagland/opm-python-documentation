.PHONY: docs view-docs check-branch

CURRENT_BRANCH := $(shell git rev-parse --abbrev-ref HEAD)
GIT_ROOT := $(shell git rev-parse --show-toplevel)

# Build the documentation locally for the current branch
# NOTE: You need to commit your changes before running this command
docs: check-branch
	sphinx-versioned -m ${CURRENT_BRANCH} -b ${CURRENT_BRANCH} --git-root ../../

# opmdoc-view-doc opens the page with the platform's own opener (xdg-open, open or start)
view-docs: check-branch
	@opmdoc-view-doc --branch=$(CURRENT_BRANCH)

test:
	pytest tests/

coverage:
	coverage run -m pytest tests
	coverage report -m

# sphinx-versioned builds branches, not commits. On a detached HEAD the branch
# name is "HEAD", which matches no branch, and `make docs` would exit 0 without
# building anything. Stop with an explanation instead.
check-branch:
	@if [ "$(CURRENT_BRANCH)" = "HEAD" ]; then \
		echo "Error: HEAD is detached. The documentation is built from a branch; check one out first." >&2; \
		exit 1; \
	fi
