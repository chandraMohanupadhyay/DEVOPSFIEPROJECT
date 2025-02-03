FROM golang:1.22.5 as base

WORKDIR /APP

COPY go.mod .

RUN go mod download 

COPY . .

RUN go build -o main .

#Final stage

FROM gcr.io/distroless/base

COPY --from=base /app/main .
Copy --from=base /app/static ./static
EXPOSE 8080
CMD ["./main"]