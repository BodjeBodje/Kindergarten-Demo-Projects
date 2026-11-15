# ---- build ----
FROM golang:1.23-alpine AS build
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download                # cached unless dependencies change
COPY . .
RUN CGO_ENABLED=0 go build -o /server .

# ---- run ----
FROM alpine:3.20
WORKDIR /app
COPY --from=build /server /app/server
# COPY .env .                      # uncomment if the app reads a .env file
EXPOSE 5001
CMD ["/app/server"]



# FROM golang:1.23.0-alpine

# WORKDIR /app

# COPY . .

# RUN go mod tidy

# EXPOSE 5001

# CMD ["go", "run", "main.go"]