Changes by Version
==================

0.30.3 (unreleased)
-------------------

- Nothing yet

0.30.2 (2018-07-13)
-------------------

- Do not log null spancontext references ([#487](https://github.com/jaegertracing/jaeger-client-java/pull/487), [@objectiser](https://github.com/objectiser))
- Fix jaeger-client dependency jaeger-thrift no-shadow artifact ([#486](https://github.com/jaegertracing/jaeger-client-java/pull/486), [@jpkrohling](https://github.com/jpkrohling))

0.30.1 (2018-07-10)
-------------------

- Add "serialVersionUID" for exceptions to avoid InvalidClassException ([#481](https://github.com/jaegertracing/jaeger-client-java/pull/481), [@quaff](https://github.com/quaff))
- Add jaeger-client module ([#479](https://github.com/jaegertracing/jaeger-client-java/pull/479), [@jpkrohling](https://github.com/jpkrohling))
- Fix wrong package declaration ([#480](https://github.com/jaegertracing/jaeger-client-java/pull/480), [@quaff](https://github.com/quaff))
- Make GuaranteedThroughputSampler public ([#457](https://github.com/jaegertracing/jaeger-client-java/pull/457), [@quaff](https://github.com/quaff))
- Fix version retrieval from jaeger.properties ([#478](https://github.com/jaegertracing/jaeger-client-java/pull/478), [@jpkrohling](https://github.com/jpkrohling))

0.30.0 (2018-07-04)
-------------------

WARNING: this release breaks compatibility with previous versions.

The most disruptive changes are:

1. The module `jaeger-core` is not bringing Thrift senders anymore. Instead, client applications
should now depend on the `jaeger-thrift` module, which will bring the `jaeger-core` transitively

1. The first step in establishing the public API was made: all classes were moved to an `internal` package,
to signal that they are not supposed to be used directly. Classes *not* in the `internal` package are part of the
new public API and compatibility should follow `semver`. Clients currently using the `Tracer.Builder` mechanism
are encouraged to switch over to the `Configuration` approach. If you face a situation that *cannot* be done with this
approach, do let us know.

1. Related to the point above: we now have also a SPI package, intended to be consumed by service providers (components
implementing `Sender`s, `Reporter`s, `Sampler`s). If you are implementing a service, do let us know! We need your
feedback before moving forward with this API.

1. Jaeger types related to the OpenTracing standard were renamed, to avoid name clashes: `io.jaegertracing.Tracer`
is now `JaegerTracer`.

Complete list of changes:

- Define some classes internal ([#470](https://github.com/jaegertracing/jaeger-client-java/pull/470), [@jpkrohling](https://github.com/jpkrohling))
- Change return types from Jaeger Span/Tracer/Context to Jaeger types ([#469](https://github.com/jaegertracing/jaeger-client-java/pull/469), [@jpkrohling](https://github.com/jpkrohling))
- Rename Jaeger's Span to JaegerSpan ([#454](https://github.com/jaegertracing/jaeger-client-java/pull/454), [@jpkrohling](https://github.com/jpkrohling))
- Upgrades internals to Zipkin v2 library ([#456](https://github.com/jaegertracing/jaeger-client-java/pull/456), [@adriancole](https://github.com/adriancole))
- Make jaeger-thrift's shaded JAR the default one ([#461](https://github.com/jaegertracing/jaeger-client-java/pull/461), [@jpkrohling](https://github.com/jpkrohling))
- Treat gauge.update() parameter as new value, not delta ([#463](https://github.com/jaegertracing/jaeger-client-java/pull/463), [@mdouaihy](https://github.com/mdouaihy)) 
- Adjust thrift shadow configuration and version ([#458](https://github.com/jaegertracing/jaeger-client-java/pull/458), [@jpkrohling](https://github.com/jpkrohling))
- Remove dependency from jaeger-core to jaeger-thrift ([#449](https://github.com/jaegertracing/jaeger-client-java/pull/449), [@jpkrohling](https://github.com/jpkrohling))

0.29.0 (2018-06-07)
-------------------

- Deprecate B3 codec contructor ([#440](https://github.com/jaegertracing/jaeger-client-java/pull/440), [@pavolloffay](https://github.com/pavolloffay))
- Add baggage to B3 codec ([#438](https://github.com/jaegertracing/jaeger-client-java/pull/438), [@pavolloffay](https://github.com/pavolloffay))
- Remove deprecated API - HttpSender and RemoteBaggageManager ([#431](https://github.com/jaegertracing/jaeger-client-java/pull/431), [@pavolloffay](https://github.com/pavolloffay))
- Load metrics factory service from classpath if available ([#433](https://github.com/jaegertracing/jaeger-client-java/pull/433), [@jpkrohling](https://github.com/jpkrohling))

0.28.0 (2018-05-24)
-------------------
- Remove unused exception ([#428](https://github.com/jaegertracing/jaeger-client-java/pull/428), [@pavolloffay](https://github.com/pavolloffay))
- Add builder patter to RemoteBaggageManager and deprecate some APIs ([#424](https://github.com/jaegertracing/jaeger-client-java/pull/424), [@pavolloffay](https://github.com/pavolloffay))
- Use string builder instead of string format ([#425](https://github.com/jaegertracing/jaeger-client-java/pull/425), [@pavolloffay](https://github.com/pavolloffay))
- Remove deprecated APIs ([#414](https://github.com/jaegertracing/jaeger-client-java/pull/414), [@pavolloffay](https://github.com/pavolloffay))
- Implement Zipkin 2 JSON Sender ([#399](https://github.com/jaegertracing/jaeger-client-java/pull/399), [@keitwb](https://github.com/keitwb))
- Fix deploy stage on travis ([#421](https://github.com/jaegertracing/jaeger-client-java/pull/421), [@pavolloffay](https://github.com/pavolloffay)) 
- Bump versions of gradle plugins ([#418](https://github.com/jaegertracing/jaeger-client-java/pull/418), [@pavolloffay](https://github.com/pavolloffay))
- Bump gradle wrapper to 4.7 ([#419](https://github.com/jaegertracing/jaeger-client-java/pull/419), [@pavolloffay](https://github.com/pavolloffay))
- Fix flaky test in RemoteReporterTest ([#415](https://github.com/jaegertracing/jaeger-client-java/pull/415), [@pavolloffay](https://github.com/pavolloffay))
- Do not use deprecated Tracer.Builder constructor internally ([#417](https://github.com/jaegertracing/jaeger-client-java/pull/417), [@pavolloffay](https://github.com/pavolloffay))
- Polish configuration API ([#411](https://github.com/jaegertracing/jaeger-client-java/pull/411), [@pavolloffay](https://github.com/pavolloffay))
- Do not use deprecated APIs internally ([#416](https://github.com/jaegertracing/jaeger-client-java/pull/416), [@pavolloffay](https://github.com/pavolloffay))
- Do not use deprecated APIs internally ([#412](https://github.com/jaegertracing/jaeger-client-java/pull/412), [@pavolloffay](https://github.com/pavolloffay))
- Remove dependency on brave-http ([#410](https://github.com/jaegertracing/jaeger-client-java/pull/410), [@pavolloffay](https://github.com/pavolloffay))
- Remove tchannel from crossdock ([#405](https://github.com/jaegertracing/jaeger-client-java/pull/405), [@yurishkuro](https://github.com/yurishkuro))
- Add Node.js client to crossdock matrix ([#404](https://github.com/jaegertracing/jaeger-client-java/pull/404), [@yurishkuro](https://github.com/yurishkuro))
- Remove tchannel as tested transport in crossdock ([#403](https://github.com/jaegertracing/jaeger-client-java/pull/403), [@yurishkuro](https://github.com/yurishkuro))
- Define dependencies versions in top level build.gradle ([#402](https://github.com/jaegertracing/jaeger-client-java/pull/402), [@objectiser](https://github.com/objectiser))

0.27.0 (2018-04-18)
-------------------

- Enable development and dependency versions to be overridden from the commandline (#397) <Gary Brown>
- Add tests for metrics exposed via prometheus (#386)  <Kevin Earls>
- Change groupid to io.jaegertracing and remove instrumentations (#375). Sources with com.uber.jaeger have been moved to https://github.com/jaegertracing/legacy-client-java <Pavol Loffay>
- Remove reference to JAEGER_DISABLE_GLOBAL_TRACER (#379) <Charlie Sharpsteen>
- Avoid direct access to apache thrift from jaeger-core via transitive dependency through jaeger-thrift (#374) <Gary Brown>
- Make some methods in HttpSender.Builder public (#376) <Pavol Loffay>

0.26.0 (2018-03-19)
-------------------

- Avoid host lookups if trace tags have already been provided (#371) <Christopher Hunt>
- Update the ReporterConfig to set Sender Correctly (#370) <Nate Hart>
- Fix for issue 366, fix deprecated code in example (#367) <Kevin Earls>

0.25.0 (2018-03-07)
-------------------

- Consolidate codec exception handling and logs exceptions (#362) <Tomasz Adamski>
- Deprecated StatsReporter (#349) <Juraci Paixão Kröhling>
- Ignores B3 headers if invalid values are provided (#355) <Juraci Paixão Kröhling>
- Refactor public constructor API (#346) <Pavol Loffay>
- Expand exception logs (#168) <Pavol Loffay>
- Deprecate JerseyServerFilter#JerseyServerFilter(Tracer, TraceContext) (#352) <Debosmit Ray>
- Micrometer support (#335) <Juraci Paixão Kröhling>
- Metrics are now consistent with Go (#335) <Juraci Paixão Kröhling>
- Updated Trace Resolver (#347) <Gary Brown>


0.24.0 (2018-01-31)
-------------------

- Remove apache instrumentation dependence on jaeger-context (#320) <Debosmit Ray>
- Remove JAX-RS2 instrumentation dependence on TracingUtils/jaeger-context (#319) <Debosmit Ray>
- Fix ClassCastException when a wrapped span impl is activated instead of the Jaeger Span (#327) <Gary Brown>
- Remove shadow dependency from jaeger-b3 (#309) <Prithvi Raj>
- Adding annotated filter priorities for Jersey filters (#329) <Debosmit Ray>
- Handle baggage null values better (#308) <Babak Mozaffari>


0.23.0 (2018-01-12)
-------------------

- Upgrade to OpenTracing API v0.31.0 (#313)


0.22.0-RC3 (2017-12-08)

- Remove dependency on GlobalTracer (#302) <Debosmit Ray>
- Add configuration support for B3 trace context propagation (#296) <Gary Brown>
- Prevent Span from being reported twice on multiple calls to finish() (#299) <Debosmit Ray>
- Do not store client span in thread-local in apache and jax-rs2 instrumentation (#297) <Debosmit Ray>
- Add auth options to HttpSender (#285) <Juraci Paixão Kröhling>


0.22.0-RC2 (2017-10-26)
-----------------------

- Break apart functionality of TracingRequestInterceptor (https://github.com/jaegertracing/jaeger-client-java/pull/248)
- Split out the jaxrs2 filters (https://github.com/jaegertracing/jaeger-client-java/pull/273)
- Add TraceContext backed by ActiveSpanSource (https://github.com/jaegertracing/jaeger-client-java/pull/266)
- Update to Apache License v. 2 (https://github.com/jaegertracing/jaeger-client-java/pull/262)
- Use io.opentracing.GlobalTracer instead of singleton in Configuration (https://github.com/jaegertracing/jaeger-client-java/pull/255)
- Tracer implements Closeable (https://github.com/jaegertracing/jaeger-client-java/pull/242)
- Fix: span builder should accept null in asChildOf (https://github.com/jaegertracing/jaeger-client-java/pull/243)


0.21.0 (2017-09-15)
-------------------
- Support baggage restrictions (https://github.com/uber/jaeger-client-java/pull/217, https://github.com/uber/jaeger-client-java/pull/229)
- Fix concurrency bug when using multiple senders (https://github.com/uber/jaeger-client-java/pull/233)
- Support span log fields in zipkin sender (https://github.com/uber/jaeger-client-java/pull/226)


0.20.6 (2017-08-01)
-------------------
- Use okhttp for HTTP sender (https://github.com/uber/jaeger-client-java/pull/224)


0.20.0 (2017-06-23)
-------------------
- Upgrade to OpenTracing Java 0.30.0 with in-process propagation support (https://github.com/uber/jaeger-client-java/pull/188)
- Add Process IP to jaeger.thrift (https://github.com/uber/jaeger-client-java/pull/197)
- Implement HTTP sender for jaeger.thrift (https://github.com/uber/jaeger-client-java/pull/194)


0.19.0 (2017-05-29)
-------------------
- TraceResolver support (https://github.com/uber/jaeger-client-java/pull/175)
- Do not truncate reported strings (https://github.com/uber/jaeger-client-java/pull/174)
- Bump OpenTracing version to 0.22.0 (https://github.com/uber/jaeger-client-java/pull/164)
- Use jaeger.thrift data model (https://github.com/uber/jaeger-client-java/pull/142)
- Enable process level tags to be associated with the tracer (https://github.com/uber/jaeger-client-java/pull/143)


0.18.0 (2017-04-13)
-------------------

- Add adaptive sampler
- Run RemoteReporter's flush timer in daemon thread (https://github.com/uber/jaeger-client-java/pull/124)
- Bump opentracingVersion to 0.21.0 (https://github.com/uber/jaeger-client-java/pull/137)
- Add Java 6 compatibility (https://github.com/uber/jaeger-client-java/pull/132)


0.17.0 (2016-12-02)
-------------------

- Fix bug where server spans were incorrectly marked as local components
- Tighten checks for marking a span as a RPC


0.16.0 (2016-11-28)
-------------------

- Add a Configuration#closeTracer() method
- Add Builder to TextMapCodec
- Bump up zipkin to 1.16.2
- Automatically add span names for jersey instrumentation


0.15.0 (2016-10-26)
-------------------

- Add init logging
- Add a Tracer.close() method
- Fill in `Host` on all annotations when reporting to Zipkin
- Downgrade to libthrift 0.9.2
- Publish a shaded jar with libthrift 0.9.2 packaged
- Bump up zipkin versions


0.14.0 (2016-10-06)
-------------------

- Fix http url tag on jaxrs2 filters
- Add convenience setter for metrics
- Expose interceptor callbacks and custom operation name for extension classes


0.13.0 (2016-09-29)
-------------------

- Fix bug with dropwizard config parsing


0.12.0 (2016-09-27)
-------------------

- Support Apache HttpClient


0.11.0 (2016-09-22)
-------------------

- fixed crossdock notImplementedError propagation
- refactored configuration
- added google-formatter


0.10.0 (2016-09-16)
-------------------

- Support debug traces via HTTP header "jaeger-debug-id"


0.9.0 (2016-09-12)
-------------------

- Introduce Clock interface for time measurements
- Use nano-time for measuring duration
- Remove powermock dependency
- Upgrade to OT 0.15


0.8.2 (2016-09-09)
-------------------

- Exclude test classes from published jars


0.8.1 (2016-09-09)
-------------------

- Default peer service name to blank as it is required in Thrift Endpoint (fixes #45)


0.8.0 (2016-09-06)
-------------------

- Add jaeger-zipkin module that allows on the wire propagation with B3-xxx headers and uses zipkin-reporter
- Report sampling strategy as root span tags `sampler.type` and `sampler.param`. In case of probabilistic sampling (most frequently used strategy), the values would be `probabilistic` and the sampling probability [0 .. 1], respectively.
- Record host name as `jaeger.hostname` tag on the first-in-process spans (i.e. root spans and rpc-server spans)
- Record the version of the Jaeger library as `jaeger.version` tag


0.7.1 (2016-08-22)
-------------------

- Reduce the size of published jars


0.7.0 (2016-08-19)
-------------------

- Upgrade to OpenTracing API 0.12, with immutable SpanContext

