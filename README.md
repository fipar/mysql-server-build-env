# mysql-server-build-env
Docker environment to build MySQL server (8.0)

Once built (see instructions in Dockerfile) you can start a container
with your local clone of mysql-server doing something like:

    docker run --rm -i --name buildenvmysql -i -v /Users/fipar/src/mysql-server:/src -v ~/tmp/build:/build fipar/mysql-server-build-env:v1 /bin/bash	

You can then attach to it

	docker exec -it buildenvmysql /bin/bash

Build MySQL as you normally would  all the meanwhile editing code on your
local machine using your editor of choice, and accessing the build on
your local /tmp/build (which, if you're not on linux, you can then
mount on another container to test the build).

        cmake . -DDOWNLOAD_BOOST=1 -DWITH_BOOST=/lib/boost/