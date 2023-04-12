- The `FROM` instruction initializes a new build stage and sets the [_Base Image_](https://docs.docker.com/glossary/#base-image) for subsequent instructions. As such, a valid `Dockerfile` must start with a `FROM` instruction
	-  `ARG` is the only instruction that may precede `FROM` in the `Dockerfile`. FROM might need to have arguments,  so to use them in docker file ARG is used as 
	```
	   ARG var_name=value
	   FROM base_image:$(var_name)
	```
	-   `FROM` can appear multiple times within a single `Dockerfile` to create multiple images or use one build stage as a dependency for another. Simply make a note of the last image ID output by the commit before each new `FROM` instruction. Each `FROM` instruction clears any state created by previous instructions.
	-   Optionally a name can be given to a new build stage by adding `AS name` to the `FROM` instruction. The name can be used in subsequent `FROM` and `COPY --from=<name>` instructions to refer to the image built in this stage.
	-   The `tag` or `digest` values are optional. If you omit either of them, the builder assumes a `latest` tag by default. The builder returns an error if it cannot find the `tag` value.
- The `COPY` instruction copies new files or directories from `<src>` and adds them to the filesystem of the container at the path `<dest>`. 
- - The `ADD` instruction copies new files, directories or remote file URLs from `<src>` and adds them to the filesystem of the image at the path `<dest>`.
- RUN instruction will execute any commands in a new layer on top of the current image and commit the results. The resulting committed image will be used for the next step in the `Dockerfile`. Using backslash \ makes command to move to the next new line.  It has 2 forms:
	- RUN \<command\>
	- RUN ["executable", "param1", "param2", ... ]
- WORKDIR The `WORKDIR` instruction sets the working directory for any `RUN`, `CMD`, `ENTRYPOINT`, `COPY` and `ADD` instructions that follow it in the `Dockerfile`. If the `WORKDIR` doesn’t exist, it will be created even if it’s not used in any subsequent `Dockerfile` instruction
- An `ENTRYPOINT` allows you to configure a container that will run as an executable.
- **The main purpose of a `CMD` is to provide defaults for an executing container.** These defaults can include an executable, or they can omit the executable, in which case you must specify an `ENTRYPOINT` instruction as well. If `CMD` is used to provide default arguments for the `ENTRYPOINT` instruction, both the `CMD` and `ENTRYPOINT` instructions should be specified with the JSON array format.
- One of the preferences of ADD is that if archived file is given, it will unarchive it and copy it, if url is given it will automatically download it, while COPY will not behave as it 
- BUILD. There are two use cases of this command:
	- docker build \<path of Dockerfile or URL (for example from github)\>
	- docker build -t  \<name\>:\<tag\> (name:tag format)




-------------------------------------------------------------------------------
[Docker]