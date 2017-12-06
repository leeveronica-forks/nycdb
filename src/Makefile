init: cython | venv
	./venv/bin/pip3 install -r requirements.txt

test:
	pytest tests/unit/

test-unit: test

test-integration:
	docker run --name nycdb-test -p 7777:5432 -e POSTGRES_PASSWORD=password -d postgres:9.6
	./scripts/wait-for-pg.sh
	./venv/bin/pytest tests/integration || true
	docker stop nycdb-test && docker rm -v nycdb-test

venv:
	python3 -m venv venv

cython: venv
	./venv/bin/pip3 install cython


.PHONY: init test test-integration test-unit cython