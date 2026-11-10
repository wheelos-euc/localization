# WheelOS Localization

Independent `wheelos_localization` Bzlmod package. It owns the Apollo component
under `modules/localization`, NDT and RTK components under
`modules/ndt_localization` and `modules/rtk_localization`, and the OpenLoc
estimator plus Cyber host support under `modules/localization/openloc` and
`modules/localization/openloc_host`. OpenLoc remains a middleware-independent
C++ library internally, not a separate Bzlmod package.

From the Apollo workspace, in the managed development container:

```bash
bazel build --config=dev -c opt @wheelos_localization//modules/localization:liblocalization_component.so
bazel test --config=dev -c opt @wheelos_localization//modules/localization/...
bazel run --config=dev -c opt @wheelos_localization//:install_dir -- --destdir /path/to/sdk
```

See [component configuration and contracts](modules/localization/README.md)
and [host build targets](modules/localization/openloc_host/BUILD).
The configuration template is deliberately non-runnable until configured.

Like `transform`, this checkout is ignored by the product repository.
Its Git source is registered in `wheelos.repos`; no Bzlmod registry release
has been published. Do not deliver only the product's source deletions.
Local overrides do not establish registry/release acceptance.
