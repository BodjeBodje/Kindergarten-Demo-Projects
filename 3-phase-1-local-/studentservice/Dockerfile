FROM golang:1.23.0-alpine

WORKDIR /app

COPY . .

RUN go mod tidy

EXPOSE 5001

CMD ["go", "run", "main.go"]