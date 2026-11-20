FROM golang:1.22 AS builder
WORKDIR /app
COPY main.go .
RUN CGO_ENABLED=0 GOOS=linux go build -o server main.go

FROM alpine:3.22
WORKDIR /app
COPY --from=builder /app/server .
USER nobody
EXPOSE 8080
ENTRYPOINT ["./server"]
