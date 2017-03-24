# Version 0.2.0 (Mar 17, 2017)

## New Features

  * Added `Client` which is created once with a stripe private key and is
    intended to be re-used for multiple requests. It implements `Sync` so you
    can share it among multiple threads.
  * Added new strongly-typed `Currency` type following the example of
    https://github.com/stripe/stripe-go.
  * `Customer::create`/`CustomerParams` now support using `CardParams` as a
    source instead of just tokens.
  * Implemented the [sources API](https://stripe.com/docs/api#sources) in the `Source` type.

## Breaking Changes

  * All `Params` types now use `&str` fields instead of `String`s.
  * Requests used to require a `stripe_key: &str` as their final argument but
    now use a `&Client` as the first argument instead.
  * Stripe tokens used to be directly used as a source in `CustomerParams` but
    now must be used with `CustomerSource::Token("tok_xyzABC123")`.

## General Improvements

  * Added remaining fields to `Params` types after switching from
    `serde_urlencoded` to `serde_qs` to support nested params.
  * Added the `create_customer` example
  * Types that implement `Deserialize` now also implement `Debug`.
  * Types that implement `Serialize` now also implement `Default`.