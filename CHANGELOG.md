# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/) and this
project adheres to [Semantic Versioning](http://semver.org/).

## [Unreleased]

### Breaking

### Changed

### Added

## [11.5.2] - 2019-06-20

### Changed

- fix: avoid mutation bug in registry

## [11.5.1] - 2019-06-13

### Changed

- fix: guard against missing constructor

## [11.5.0] - 2019-06-04

### Added

- Added `timestamps` toggle to `collectDefaultMetrics` options
- Export `validateMetricName`

## [11.4.0] - 2019-06-04

### Added

- `nodejs_active_handles` metric to the `collectDefaultMetrics()`. Unlike `nodejs_active_handles_total` it split count of active handles by type.
- `nodejs_active_requests` metric to the `collectDefaultMetrics()`. Unlike `nodejs_active_requests_total` it split count of active requests by type.

## [11.3.0] - 2019-04-02

### Changed

- Check that cluster worker is still connected before attempting to query it for
  metrics. (#244)

### Added

- Added a `remove()` method on each metric type, based on [Prometheus "Writing Client Libraries" section on labels](https://prometheus.io/docs/instrumenting/writing_clientlibs/#labels)

## [11.2.1]

### Breaking

### Changed

### Added

- Updated types for Summary in typescript definition file

## [11.2.0]

### Changed

- Updated child dependency `merge` patch version to remove vulnerability.

### Added

- Added an initial `benchmark` suite which can be run with `npm run benchmarks`.
- Add support for sliding windows in Summaries

## [11.1.3] - 2018-09-22

### Changed

- Fixed performance by avoiding `Object.assign` on hot paths, as well as
  mutating objects when appropriate.

## [11.1.2] - 2018-09-19

### Changed

- Allow setting Gauge values to NaN, +Inf, and -Inf
- Fixed `histogram` scrape performance by using `acc.push` instead of `acc.concat`. Fixes #216 with #219

## [11.1.1] - 2018-06-29

### Changed

- Fixed `processOpenFileDescriptors` metric when no custom config was set

## [11.1.0] - 2018-06-29

- Added ability to set a name prefix in the default metrics

### Changed

- Fixed `startTimer` utility to not mutate objects passed as `startLabels`
- Fixed `Counter` to validate labels parameter of `inc()` against initial
  labelset
- Fixed `AggregatorFactory` losing the aggregator method of metrics

## [11.0.0] - 2018-03-10

### Breaking

- Fixed `gauge.setToCurrentTime()` to use seconds instead of milliseconds
  - This conforms to Prometheus
    [best practices](https://prometheus.io/docs/practices/naming/#base-units)
- Dropped support for node 4

## [10.2.3] - 2018-02-28

### Breaking

### Changed

- Fixed issue that `registry.getMetricsAsJSON()` ignores registry default labels

### Added

## [10.2.2] - 2017-11-02

### Changed

- Fixed invalid `process_virtual_memory_bytes` reported under linux

## [10.2.1] - 2017-10-27

### Changed

- Only resolve/reject `clusterMetrics` promise if no callback is provided

## [10.2.0] - 2017-10-16

### Changed

- Don't add event listeners if cluster module is not used.
- Fixed issue with counters having extra records when using empty labels

### Added

- Added `reset` to Counter and Gauge
- Added `resetMetrics` to register to calling `reset` of all metric instances

## [10.1.1] - 2017-09-26

### Changed

- Update TypeScript definitions and JSDoc comments to match JavaScript sources
- Fix lexical scope of `arguments` in cluster code

## [10.1.0] - 2017-09-04

### Added

- Support aggregating metrics across workers in a Node.js cluster.

## [10.0.4] - 2017-08-22

### Changed

- Include invalid values in the error messages

## [10.0.3] - 2017-08-07

### Added

- Added registerMetric to definitions file

### Changed

- Fixed typing of DefaultMetricsCollectorConfiguration in definitions file
- Don't pass timestamps through to pushgateway by default

## [10.0.2] - 2017-07-07

### Changed

- Don't poll default metrics every single tick

## [10.0.1] - 2017-07-06

### Added

- Metrics should be initialized to 0 when there are no labels

## [10.0.0] - 2017-07-04

### Breaking

- Print deprecation warning when metrics are constructed using non-objects
- Print deprecation warning when `collectDefaultMetrics` is called with a number

### Added

- Ability to set default labels by registry
- Allow passing in `registry` as second argument to `collectDefaultMetrics` to
  use that instead of the default registry

### Changed

- Convert code base to ES2015 code (node 4)
  - add engines field to package.json
  - Use object shorthand
  - Remove `util-extend` in favor of `Object.assign`
  - Arrow functions over binding or putting `this` in a variable
  - Use template strings
  - `prototype` -> `class`

## [9.1.1] - 2017-06-17

### Changed

- Don't set timestamps for metrics that are never updated

## [9.1.0] - 2017-06-07

### Added

- Ability to merge registries

### Changed

- Correct typedefs for object constructor of metrics

## [9.0.0] - 2017-05-06

### Added

- Support for multiple registers
- Support for object literals in metric constructors
- Timestamp support

### Changed

- Collection of default metrics is now disabled by default. Start collection by
  running `collectDefaultMetrics()`.

### Deprecated

- Creating metrics with one argument per parameter - use object literals
  instead.

[unreleased]: https://github.com/siimon/prom-client/compare/v10.2.2...HEAD
[10.2.2]: https://github.com/siimon/prom-client/compare/v10.2.1...v10.2.2
[10.2.1]: https://github.com/siimon/prom-client/compare/v10.2.0...v10.2.1
[10.2.0]: https://github.com/siimon/prom-client/compare/v10.1.1...v10.2.0
[10.1.1]: https://github.com/siimon/prom-client/compare/v10.1.0...v10.1.1
[10.1.0]: https://github.com/siimon/prom-client/compare/v10.0.4...v10.1.0
[10.0.4]: https://github.com/siimon/prom-client/compare/v10.0.3...v10.0.4
[10.0.3]: https://github.com/siimon/prom-client/compare/v10.0.2...v10.0.3
[10.0.2]: https://github.com/siimon/prom-client/compare/v10.0.1...v10.0.2
[10.0.1]: https://github.com/siimon/prom-client/compare/v10.0.0...v10.0.1
[10.0.0]: https://github.com/siimon/prom-client/compare/v9.1.1...v10.0.0
[9.1.1]: https://github.com/siimon/prom-client/compare/v9.1.0...v9.1.1
[9.1.0]: https://github.com/siimon/prom-client/compare/v9.0.0...v9.1.0
[9.0.0]: https://github.com/siimon/prom-client/commit/1ef835f908e1a5032f228bbc754479fe7ccf5201
