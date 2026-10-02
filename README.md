<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# truncsdf

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Round a single-precision floating-point number to the nearest number toward zero with `n` significant figures.

<section class="intro">

The function rounds a single-precision floating-point number to the specified number of [significant figures][significant-figures] toward zero.

<!-- <equation class="equation" label="eq:truncsd_function" align="center" raw="y = \operatorname{trunc}\left(x \cdot b^{n - \lfloor \log_b |x| \rfloor - 1}\right) \cdot b^{\lfloor \log_b |x| \rfloor - n + 1}" alt="Truncate to n significant figures"> -->

```math
y = \mathop{\mathrm{trunc}}\left(x \cdot b^{n - \lfloor \log_b |x| \rfloor - 1}\right) \cdot b^{\lfloor \log_b |x| \rfloor - n + 1}
```

<!-- <div class="equation" align="center" data-raw-text="y = \operatorname{trunc}\left(x \cdot b^{n - \lfloor \log_b |x| \rfloor - 1}\right) \cdot b^{\lfloor \log_b |x| \rfloor - n + 1}" data-equation="eq:truncsd_function">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@b41c953b185783768ac50677b4e07eeae0b84cdc/lib/node_modules/@stdlib/math/base/special/truncsdf/docs/img/equation_truncsd_function.svg" alt="Truncate to n significant figures">
    <br>
</div> -->

<!-- </equation> -->

</section>

<!-- /.intro -->

<section class="installation">

## Installation

```bash
npm install @stdlib/math-base-special-truncsdf
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var truncsdf = require( '@stdlib/math-base-special-truncsdf' );
```

#### truncsdf( x, n, b )

Rounds a single-precision floating-point number to the nearest number toward zero with `n` significant figures.

```javascript
var v = truncsdf( 3.1415927410125732, 5, 10 );
// returns 3.1414999961853027

v = truncsdf( 3.1415927410125732, 1, 10 );
// returns 3.0

v = truncsdf( 12368.0, 2, 10 );
// returns 12000.0

v = truncsdf( 0.0313, 2, 2 );
// returns 0.03125
```

</section>

<!-- /.usage -->

<section class="notes">

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var uniform = require( '@stdlib/random-array-uniform' );
var logEachMap = require( '@stdlib/console-log-each-map' );
var truncsdf = require( '@stdlib/math-base-special-truncsdf' );

var opts = {
    'dtype': 'float32'
};
var x = uniform( 100, -5000.0, 5000.0, opts );

logEachMap( 'x: %0.4f. n: %d. b: %d. Rounded: %0.4f.', x, 5, 10, truncsdf );
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->

* * *

<section class="c">

## C APIs

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- C usage documentation. -->

<section class="usage">

### Usage

```c
#include "stdlib/math/base/special/truncsdf.h"
```

#### stdlib_base_truncsdf( x, n, b )

Rounds a single-precision floating-point number to the nearest number toward zero with `n` significant figures.

```c
float out = stdlib_base_truncsdf( 3.141592653589793f, 3, 10 );
// returns ~3.14f

out = stdlib_base_truncsdf( 12368.0f, 2, 10 );
// returns 12000.0f
```

The function accepts the following arguments:

-   **x**: `[in] float` input value.
-   **n**: `[in] int32_t` number of significant figures.
-   **b**: `[in] int32_t` base.

```c
float stdlib_base_truncsdf( const float x, const int32_t n, const int32_t b );
```

</section>

<!-- /.usage -->

<!-- C API usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- C API usage examples. -->

<section class="examples">

### Examples

```c
#include "stdlib/math/base/special/truncsdf.h"
#include <stdio.h>

int main( void ) {
    const float x[] = { 3.14f, -3.14f, 0.0f, 0.0f/0.0f };

    float y;
    int i;
    for ( i = 0; i < 4; i++ ) {
        y = stdlib_base_truncsdf( x[ i ], 2, 10 );
        printf( "truncsdf(%f, 2, 10) = %f\n", x[ i ], y );
    }
}
```

</section>

<!-- /.examples -->

</section>

<!-- /.c -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/math-base-special-truncsdf.svg
[npm-url]: https://npmjs.org/package/@stdlib/math-base-special-truncsdf

[test-image]: https://github.com/stdlib-js/math-base-special-truncsdf/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/math-base-special-truncsdf/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/math-base-special-truncsdf/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/math-base-special-truncsdf?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/math-base-special-truncsdf.svg
[dependencies-url]: https://david-dm.org/stdlib-js/math-base-special-truncsdf/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/math-base-special-truncsdf/tree/deno
[deno-readme]: https://github.com/stdlib-js/math-base-special-truncsdf/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/math-base-special-truncsdf/tree/umd
[umd-readme]: https://github.com/stdlib-js/math-base-special-truncsdf/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/math-base-special-truncsdf/tree/esm
[esm-readme]: https://github.com/stdlib-js/math-base-special-truncsdf/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/math-base-special-truncsdf/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/math-base-special-truncsdf/main/LICENSE

[significant-figures]: https://en.wikipedia.org/wiki/Significant_figures

<!-- <related-links> -->

<!-- </related-links> -->

</section>

<!-- /.links -->
