# `navigator` API registry

The purpose of this repo is to track Web-interop details related to the global `navigator` and its various properties/methods.

## Registry

- **[`userAgent`](https://html.spec.whatwg.org/multipage/#dom-navigator-useragent)**

  This property is incorporated into the WinterCG Common Minimum API, and
  implementations should follow
  [the requirements listed there](https://common-min-api.proposal.wintercg.org/#requirements-for-navigatoruseragent).

- **[`appCodeName`, `appName`, `appVersion`, `platform`, `product`,
  `productSub`, `vendor`, `vendorSub`, `taintEnabled()`, `oscpu`
  ](https://html.spec.whatwg.org/multipage/#client-identification)**

  Web-interoperable runtimes other than web browsers should not implement these
  APIs. If they do so, they use a consistent
  [navigator compatibility mode](https://html.spec.whatwg.org/multipage/#concept-navigator-compatibility-mode),
  and they must implement all listed APIs (if applicable to the compatibility
  mode). Additionally, their value of `navigator.userAgent` should also be
  consistent with web browsers of the same navigator compatibility mode.

- **[`language`, `languages`](https://html.spec.whatwg.org/multipage/#language-preferences)**

  Web-interoperable runtimes whose natural language (e.g. in UI or error
  messages) can be switched by the user (such as browsers) should implement
  these properties. Runtimes which don't have such a concept but can run in a
  platform which does have it (such as the OS's default language, for a CLI
  runtime) may implement them as well, if other platform details are exposed to
  author code through other means. Other runtimes should not implement it, but
  if they do, they must use `"en-US"` as the single
  [plausible language](https://html.spec.whatwg.org/multipage/#a-plausible-language).

  Runtimes which implement these properties should also support the
  [`languagechange`](https://html.spec.whatwg.org/multipage/#event-languagechange)
  event.

- **[`onLine`](https://html.spec.whatwg.org/multipage/#navigator.online)**

  Web-interoperable runtimes which are expected to be permanently online
  (i.e. network servers) or permanently offline should not implement this
  property. Other runtimes may do so. Any runtimes that implement it should also
  support the [`online`](https://html.spec.whatwg.org/multipage/#event-online)
  and [`offline`](https://html.spec.whatwg.org/multipage/#event-offline) events.

- **[`hardwareConcurrency`](https://html.spec.whatwg.org/multipage/#navigator.hardwareconcurrency)**

  Web-interoperable runtimes which support web workers should implement this
  property. Other runtimes should not implement it, but if they do, it should
  return 1.

- **[`registerProtocolHandler()`, `unregisterProtocolHandler()`](https://html.spec.whatwg.org/multipage/#custom-handlers)**

  Runtimes other than browsers should not implement these methods. (The
  assumption is that these methods would be useless to such runtimes, since they
  would not have any equivalent to navigation.)

- **[`cookieEnabled`](https://html.spec.whatwg.org/multipage/system-state.html#cookies)**

  Runtimes other than browsers should not support this property. (The assumption
  is that no such runtimes would have support for a cookie jar in their `fetch`
  implementation, or directly support cookies in any other way.)

- **[`plugins`, `mimeTypes`, `javaEnabled()`, `pdfViewerEnabled`](https://html.spec.whatwg.org/multipage/#pdf-viewing-support)**

  Runtimes other than browsers should not support these properties or methods.
  (The assumption is that no such runtimes would have support for PDF viewing.)
