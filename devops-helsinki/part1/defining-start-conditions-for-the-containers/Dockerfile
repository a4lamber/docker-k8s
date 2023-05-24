FROM ubuntu:18.04

WORKDIR /mydir

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y curl

RUN curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl

# add permissions
RUN chmod a+rx /usr/local/bin/youtube-dl

RUN apt-get install -y python

# In Dockerfile, "ENV a b" is same as "RUN export a=b" but more readible
ENV LC_ALL C.UTF-8

# CMD will be overwritten by argument you pass in such as
#    docker container run youtube-dl <argument>
# example:
#    docker container run youtube-dl pwd

# ENTRYPOINT will combine the <entrypoint> with the <argument>

# IF both passed in <ENTRYPOINT> <CMD>


# CMD ["/usr/local/bin/youtube-dl"]

ENTRYPOINT ["/usr/local/bin/youtube-dl"]
CMD ["https://imgur.com/JY5tHqr"]

