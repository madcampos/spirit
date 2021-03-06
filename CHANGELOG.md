## v0.2.0
#### Release Date: 08-29-2016
- API has underwent minor changes:
  - `spirit.is_promise` is still there, but no longer covered under docs (considered internal api)
  - _All_ API under `spirit.node.utils` is now considered internal, they are still documented however
  - `spirit.node.is_Response` has moved to `spirit.node.utils.is_Response`
  - `spirit.node.middlewares` are moved to `spirit-common`.

The reason for the change is to slim down the public API to only the essentials. The functions affected were all utility functions (and simple in functionality) and mostly used internally, but was and still is provided as a convenience.

- `**` spirit.node.adapter initialized middlewares on every request, this wasn't intended, it's been changed.

- `**` spirit.compose didn't pass arguments (other than the first) along to the next middleware, this wasn't intended, it's been changed.

- New module for bootstrapping common middleware `spirit-common`, instead of pulling in 3, 4, 5 middleware all the time, just pull in one which sets it all up.

`**` These changes are not considered a bug as all previous versions supported this, so no patch for v0.1.x. Instead it's considered a breaking change and added to v0.2.0.

Other official spirit libraries are updated to support this release (they are scheduled to be released after this spirit release):
- spirit-router -> v0.2.x
- spirit-express -> v0.2.x
- spirit-common -> v0.1.x (first version)

## v0.1.2
#### Release Date: 08-18-2016
- Added Response.cookie
- Removed Response.location
- Fix Response.attachment wasn’t returning itself (this)
- Fix When production ENV was set and an error occured in which http adapter had to handle, it would strip the body but not it’s Content-Length. This would make it seem like the request froze (or client froze).
