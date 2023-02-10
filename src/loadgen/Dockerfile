FROM alpine:3.16

RUN apk add curl bash fortune

COPY loadgen.sh .
RUN chmod +x ./loadgen.sh

CMD [ "./loadgen.sh" ]
