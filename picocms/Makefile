.PHONY: build run clean

IMG="picocms"
APP="pico"

build:
	@docker build -t $(IMG) .

run:
	@docker run --rm --name $(APP) -p 127.0.0.1:8080:80 -v ${PWD}/content:/var/www/html/content/:ro -d $(IMG)

clean:
	@docker stop $(APP) || true
	@docker rm $(APP) || true
