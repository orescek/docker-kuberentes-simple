FROM golang:1.8

WORKDIR /app
ADD digitalsignage_linux_64 /app/digitalsignage_linux_64
EXPOSE 4000

RUN chmod +x /app/digitalsignage_linux_64

CMD ["/app/digitalsignage_linux_64"]