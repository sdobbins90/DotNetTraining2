
# Container 1 will have the stuff to build our application
FROM ubuntu:20.04 as build
RUN apt-get update && apt-get install -y build-essential
WORKDIR /app
COPY src/hello.c /app/
RUN gcc -o hello -static hello.c


# "final" container will have just our compiled application.
FROM scratch as final
WORKDIR /app/
COPY --from=build /app/hello ./
ENTRYPOINT ["/app/hello"]