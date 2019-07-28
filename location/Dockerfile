FROM golang:1.12 as gobuilder
RUN mkdir /app
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY main.go .
RUN GOOS=linux CGO_ENABLED=0 go build -o location

FROM scratch
COPY --from=gobuilder /app/location location
COPY index.html .

CMD ["./location"]
