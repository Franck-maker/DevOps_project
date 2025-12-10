# Build stage

FROM golang:1.21-alpine AS builder
WORKDIR /app
COPY . .
# static compilation to avoid library issues
RUN CGO_ENABLED=0 GOOS=linux go build -o main .

# Run stage (Distroless ou Alpine pour la légèreté)

FROM alpine:latest
WORKDIR /root/
COPY --from=builder /app/main .
EXPOSE 8080
CMD ["./main"]