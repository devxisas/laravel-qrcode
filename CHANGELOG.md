# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 1.0.0 (2026-03-18)


### Features

* add artisan command for QR code generation ([5eaceb5](https://github.com/devxisas/qr-studio/commit/5eaceb5dab42b94b80789a3d24ca70685bb859a8))
* add core QR code generator with image handling ([a52adca](https://github.com/devxisas/qr-studio/commit/a52adca6501bd31cbd41900681792f7ff2e94645))
* add data types for QR code content encoding ([876ec24](https://github.com/devxisas/qr-studio/commit/876ec249c34dd42b76b1ee95f74fd9187e4fde6a))
* add GD fallback for PNG and PointyEye support from BaconQrCode 3.x ([62f6bbb](https://github.com/devxisas/qr-studio/commit/62f6bbb11b1f55ec6217366f9324e493e4b4ac1f))
* add Laravel 13 / orchestra testbench 11 support ([2abe59a](https://github.com/devxisas/qr-studio/commit/2abe59a1b2de23ec81d42c5631a596d61b27f1bf))
* add package configuration file ([0d75291](https://github.com/devxisas/qr-studio/commit/0d752911831acc5585523e892bb90881ae7b8f59))
* add QR code enums for format, style, and error correction ([34f1379](https://github.com/devxisas/qr-studio/commit/34f13796c47a32b74b8600454a3294c7fc694ac0))
* add WhatsApp data type, saveToDisk(), themes, and config expansion ([34accc0](https://github.com/devxisas/qr-studio/commit/34accc081be268de45203f274b82742447183a6f))
* redesign HasQrCode trait with qrCodeType()/qrCodeData() API and update README ([02f639c](https://github.com/devxisas/qr-studio/commit/02f639cbd0c0f3deef683235d8556ea4270d7d8b))
* register Laravel service provider and QrCode facade ([163661a](https://github.com/devxisas/qr-studio/commit/163661a9779315adbc916f54bbf70e3f52a69415))
* rename package to devxisas/qr-studio and add HasQrCode trait ([d1e78a8](https://github.com/devxisas/qr-studio/commit/d1e78a82373835330b5a15ef6600aaf75ccae560))
* respect config defaults in Blade directive, response macro, and encoding ([1b23f52](https://github.com/devxisas/qr-studio/commit/1b23f52cdb3fde75f87e86550b4bbef57bd39397))


### Bug Fixes

* [@qrcode](https://github.com/qrcode) directive wraps PNG output in &lt;img data-uri&gt; instead of echoing raw binary ([ad35fb4](https://github.com/devxisas/qr-studio/commit/ad35fb4a5513ba6269aaa7f6b1b1b5e9190cf65c))
* **bacon:** replace deprecated DEFAULT_BYTE_MODE_ECODING with DEFAULT_BYTE_MODE_ENCODING ([98cc2a8](https://github.com/devxisas/qr-studio/commit/98cc2a8a562216b57aa062fdc124c40e81866cae))
* **ci:** drop Laravel 10 support (EOL) and update illuminate/contracts constraint ([c8eb4bc](https://github.com/devxisas/qr-studio/commit/c8eb4bc55ff32c7da23019a14665f77477fed731))
* **ci:** remove Laravel 13 until pest-plugin-laravel adds support ([569d1e3](https://github.com/devxisas/qr-studio/commit/569d1e30a43b3b37de2609e6a2e9d9c3e69197cc))
* **deps:** allow larastan ^3.0 to support Laravel 12 ([284361d](https://github.com/devxisas/qr-studio/commit/284361da1f62f66a5808892333f76a133b151006))
* **deps:** upgrade phpstan ecosystem to v2 and add Laravel 13 support ([08d150c](https://github.com/devxisas/qr-studio/commit/08d150c78d7c38055c0cd26b6e1c37fb31afe9aa))
* don't prepend base_path() when merge() receives an absolute path ([01eb4e9](https://github.com/devxisas/qr-studio/commit/01eb4e956c58e05e6a3823ee39dada4f82d4a50b))
* **mecard:** do not escape colons in URL field — prevents https:// becoming https\:// ([038db02](https://github.com/devxisas/qr-studio/commit/038db02c9cf603d4c1fea43a673b0cdb1288ab5e))
* **tests:** remove missing Feature test directory from phpunit.xml ([ad304bc](https://github.com/devxisas/qr-studio/commit/ad304bc7048f82a2aea136b3656adff64d6da273))


### CI/CD

* add GitHub Actions workflows for tests and code style ([8bf887c](https://github.com/devxisas/qr-studio/commit/8bf887c931aa41c7def652a5634325f97d67044d))
* point release-please to config and manifest files ([7b924b6](https://github.com/devxisas/qr-studio/commit/7b924b64e75c8b1b7117016e9afc57500077a4b2))

## [Unreleased]

### Added
- `EyeStyle::Pointy` — new eye style from BaconQrCode 3.x (curved outer corner + circle inner)
- `GDLibRenderer` fallback for PNG when `ext-imagick` is not installed

### Fixed
- Replaced deprecated `Encoder::DEFAULT_BYTE_MODE_ECODING` (typo) with `Encoder::DEFAULT_BYTE_MODE_ENCODING`
- `getWriter()` now accepts `RendererInterface` instead of the concrete `ImageRenderer`

## [1.0.0] - 2026-03-17

### Added
- QR code generator with fluent chainable API via `QrCode` facade
- SVG, EPS, and PNG output formats (`Format` enum)
- Module styles: square, dot, round (`Style` enum) with configurable size parameter
- Eye styles: square, circle (`EyeStyle` enum)
- Gradient support with 5 types: horizontal, vertical, diagonal, inverse_diagonal, radial (`GradientType` enum)
- Error correction levels L / M / Q / H (`ErrorCorrection` enum)
- Foreground, background, and per-eye color customization
- Image merging (logo overlay) via `merge()` and `mergeString()` — PNG only
- `toDataUri()` for base64 data URI output (ideal for emails and PDFs)
- Data types: Email, PhoneNumber, SMS, Geo, WiFi, BTC, VCard 3.0, MeCard, CalendarEvent (iCal)
- `@qrcode` Blade directive with optional format and size parameters
- `response()->qrcode()` macro for HTTP streaming with correct `Content-Type`
- `php artisan qrcode:generate` Artisan command with `--format`, `--size`, `--margin`, `--error-correction`, `--output` options
- Publishable `config/laravel-qrcode.php` for package-wide defaults
- Automatic state reset after every `generate()` call
- Laravel 11 and 12 support, PHP 8.2+
- Full PHPStan level analysis and Pint code style enforcement
- Pest unit test suite

[Unreleased]: https://github.com/devxisas/laravel-qrcode/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/devxisas/laravel-qrcode/releases/tag/v1.0.0
