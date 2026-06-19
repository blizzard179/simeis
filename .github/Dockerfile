FROM rust:1.85.0-bookworm AS builder

WORKDIR /app
COPY . .
RUN cargo build --release -p simeis-server

FROM debian:bookworm-slim

RUN apt-get update && apt-get install -y --no-install-recommends ca-certificates && rm -rf /var/lib/apt/lists/*

COPY --from=builder /app/target/release/simeis-server /usr/local/bin/simeis-server

ENTRYPOINT ["simeis-server"]
