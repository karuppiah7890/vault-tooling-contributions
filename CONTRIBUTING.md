# vault-tooling-contributions

This repo details out the kind of contributions one can make to the Vault tools that I have created. Since most of the contributions seemed very similar / common, I figured I'll just create one repository to detail out the contributions one can make to all the Vault tools

# Pre-requisites

- Knowledge around Vault and Vault APIs. This is not so hard, but it's a good to have if you want to make changes to the core features of the tools

- Knowlege around Golang
  - Golang Syntax and Concepts
  - Building Golang Code (`go build` etc)
  - Testing Golang Code (`go test` etc). Though as of this writing, there are NO tests, which I understand is a very BAD thing
  - Go Modules (`go mod`, `go get`, `go.mod`, `go.sum` etc) and Golang Packages

Again, Golang is not so hard, but it's a good to have if you want to make any changes to the tools as the tools are written in Golang and use the Official Vault Golang Package. Golang is easy to learn and pickup though, compared to many other languages out there. So, don't worry if you don't know Golang :) And if you already know some language, Golang is way more easier to learn and pickup :)

# Kind of Contributions One Can Make

Basic ones
- Update Golang Version
  - This would probably bring changes in
    - `go.mod` and/ `go.sum`. Especially the line that says `go x.y.z` in `go.mod`
    - Golang Code itself
- Update Vault HTTP API Client Golang Package Version (`github.com/hashicorp/vault/api`)
  - This would bring minor changes or major breaking changes to the usage of the package, depending on the Golang package version upgrade. What this would help in is - Support more Vault versions in case there are changes in the Vault HTTP API in the newer Vault versions. Remember that Vault version is different from the Vault HTTP API version and Vault HTTP API may not change though Vault can have changes. And if HTTP API hasn't changed - ideally HTTP API behaviour also shouldn't have changed but that may not be the case always though. HTTP API change means - change in the HTTP API - change in HTTP request path, say some version mentioned changing, or something changing in it, change in HTTP request method, change in request headers, change in request body, or change in HTTP response code, change in HTTP response headers, change in HTTP response body. The Vault HTTP API Golang Package refers to the Golang Package that provides a Golang API for the Vault's HTTP API, so that it's easy to write Golang code using the Golang API to make HTTP API calls. So it's basically a Golang Package providing a Golang API which acts as a specific HTTP Client for Vault HTTP API. Note that it's a specific HTTP Client. And, if Vault HTTP API has changes, the official Vault team will also make those changes in the Vault HTTP API Client Golang Package, so we would need those :)

These basic ones could be automated to some extent, if there are no breaking changes in the change. So, that's also a thing one can do. As of now, it's all manual only

Intermediate ones
- Automate version upgrade / update for Golang version for non breaking upgrades / updates
- Automate version upgrade / update for Vault HTTP API Client Golang Package version for non breaking upgrades / updates
- Add tests
  - Integration tests with actual Vault running. Maybe use some tools and/ libraries and/ frameworks for this integration test, for example https://testcontainers.com is a great library for this :)
  - Unit tests, if any is needed, for basic small functions like utility functions etc
  - E2E tests. This might look a bit similar to Integration tests in this case. But something to consider and see how we can differentiate the two

- Improve performance
  - This is not too important for most cases. But sometimes people have Vault systems with lots of data that it becomes important to optimize the tools and improve their performance so that they work faster and better and also smoothly - without using up too much resources - compute, network, storage. Especially not use too much compute - CPU and yeah, not use too much RAM too. And if it does use too much CPU and RAM, and it does need to use it, it better use it pretty quickly and release it all :) So, that would mean that the execution time has to be pretty low
    - One could consider using Go Routines for speeding things up
    - One could consider using Golang Profiling Tools to Profile CPU, RAM and improve the CPU and RAM usage especially for the critical parts of the tool, which is usually the core functionality of the tool, apart from things like it's interface (CLI etc) work
