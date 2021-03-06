FLAGS=


flake:
	flake8 client server engine tests

setup:
	pip install -Ue .

test: flake
	py.test -s --tb=native $(FLAGS) tests

vtest: flake
	py.test -s -v --tb=native $(FLAGS) tests

cov cover coverage: flake
	coverage erase
	py.test -s --cov client --cov engine --cov server \
		--cov-config .coveragerc \
		--tb=native --cov-report html $(FLAGS) tests
	echo "open file://`pwd`/htmlcov/index.html"

cov-all: flake
	coverage erase
	py.test -s --cov client --cov engine --cov server --cov tests \
		--tb=native --cov-report html $(FLAGS) tests
	echo "open file://`pwd`/htmlcov/index.html"

clean:
	rm -rf `find . -name __pycache__`
	rm -f `find . -type f -name '*.py[co]' `
	rm -f `find . -type f -name '*~' `
	rm -f `find . -type f -name '.*~' `
	rm -f `find . -type f -name '@*' `
	rm -f `find . -type f -name '#*#' `
	rm -f `find . -type f -name '*.orig' `
	rm -f `find . -type f -name '*.rej' `
	rm -f .coverage
	rm -rf coverage
	rm -rf build
	rm -rf cover
	python setup.py clean

.PHONY: flake test vtest cov clean doc