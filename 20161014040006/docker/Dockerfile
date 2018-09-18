FROM bitwalker/alpine-elixir:1.5 as build

COPY . .

RUN export MIX_ENV=prod && \
  rm -Rf _build && \
  mix deps.get && \
  mix release

RUN APP_NAME="clock" && \
  RELEASE_DIR=`ls -d _build/prod/rel/$APP_NAME/releases/*/` && \
  mkdir /export && \
  tar -xf "$RELEASE_DIR/$APP_NAME.tar.gz" -C /export


FROM pentacent/alpine-erlang-base:latest

COPY --from=build  /export/ .

USER default

ENTRYPOINT ["/opt/app/bin/clock"]
CMD ["foreground"]
