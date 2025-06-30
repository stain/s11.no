# s11.no

This is the [Hugo](https://gohugo.io/) source code for the website hosted on <https://s11.no/> which is by and about Stian Soiland-Reyes <https://orcid.org/0000-0001-9842-9718>.

## Build

Use [Hugo 0.145](https://github.com/gohugoio/hugo/releases/tag/v0.145.0) or newer

```shell
$ hugo version
hugo v0.145.0-666444f0a52132f9fec9f71cf25b441cc6a4f355+extended linux/amd64 BuildDate=2025-02-26T15:41:25Z VendorInfo=gohugoio
```

To build and test locally, try:

```
make server
```

To deploy, you need to first mount `/files` from the s11 webserver, then either `make dev` or `make prod` depending on desired vhost.


## License

[themes](themes/) include [ronu-hugo-theme](https://github.com/softwareyoga/ronu-hugo-theme) by Deepak Karanth which is distributed under the [MIT license](https://github.com/softwareyoga/ronu-hugo-theme/blob/master/LICENSE).

[layouts/](layouts/) and [assets](assets/) are extending ronu-hugo-theme, and is likewise distributed under the [MIT license](https://spdx.org/licenses/MIT).

License of [content/](content/) and [static/](static/), unless otherwise noted, is [CC-BY-SA 4.0](https://spdx.org/licenses/CC-BY-SA-4.0.html):

©️ 2005–2025 The University of Manchester, UK  
©️ 1995–2025 Stian Soiland-Reyes <https://orcid.org/0000-0001-9842-9718>

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by-sa.svg" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
