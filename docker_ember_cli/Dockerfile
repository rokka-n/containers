FROM node:latest 
MAINTAINER Roman Naumenko <roman@naumenko.ca>

EXPOSE 4200 35729
WORKDIR /myapp

# run ember server on container start
ENTRYPOINT ["/usr/local/bin/ember"]
CMD ["server"]

RUN \
	npm install -g ember-cli&&\
	npm install -g bower &&\
	npm install -g phantomjs

# install watchman
RUN \
	git clone https://github.com/facebook/watchman.git &&\
	cd watchman &&\
	git checkout v3.5.0 &&\
	./autogen.sh &&\
	./configure &&\
	make &&\
	make install
