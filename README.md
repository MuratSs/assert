[![Go version](https://img.shields.io/badge/go-~%3E1.12.0-green.svg)](https://golang.org/doc/devel/release.html#go1.12)

# assert

Lightweight assertion library based on the fluent interface from
[assertj](http://joel-costigliola.github.io/assertj/)

## Features

The matchers included in our `assert` library are fully compatible with, and
depend on the standard Go [testing package](https://golang.org/pkg/testing/).
These just add a little syntactic sugar on top of the familiar test patterns.

To use the example from the testing documentation, here is how one would
normally write a test in Go:

```go
func TestAbs(t *testing.T) {
    got := Abs(-1)
    if got != 1 {
        t.Errorf("Abs(-1) = %d; want 1", got)
    }
}
```

With the matchers included in our `assert` package, one would write:

```go
import "github.com/MuratSs/assert"

func TestAbs(t *testing.T) {
    got := Abs(-1)
    assert.With(t).
        That(got).
        IsEqualTo(1)
}
```

This is much more readable and ultimately leads to more maintainable code.

## Usage

The matchers currently included in the `assert` package are:

1. IsEmpty/IsNotEmpty

    ```go
    func TestIsEmpty(t *testing.T) {
        s := ""
        assert.With(t).
            That(s).
            IsEmpty()
    }
    ```
    
    ```go
    func TestIsNotEmpty(t *testing.T) {
        s := "foobar"
        assert.With(t).
            That(s).
            IsNotEmpty()
    }
    ```

1. IsEqualTo

    ```go
    func TestEquals(t *testing.T) {
        got := Abs(-1)
        assert.With(t).
            That(got).
            IsEqualTo(1)
    }
    ```

1. IsGreaterThan

    ```go
    func TestIsEmpty(t *testing.T) {
        x := 1
        assert.With(t).
            That(x).
            IsGreaterThan(0)
    }
    ```

1. IsNil/IsNotNil

    ```go
    func TestIsNil(t *testing.T) {
        var s *string
        assert.With(t).
            That(s).
            IsNil()
    }
    ```

    ```go
    func TestIsNotNil(t *testing.T) {
        var s string
        assert.With(t).
            That(s).
            IsNotNil()
    }
    ```

1. IsOk

    ```go
    func TestIsOk(t *testing.T) {
        f, err := io.Open("filename.ext")
        assert.With(t).
            That(err).
            IsOk()
    }
    ```

1. ThatPanics

    ```go
    func TestThatPanics(t *testing.T) {
        f := func() {
            panic("error")
        }
        assert.With(t).
            ThatPanics(f)
    }
    ```

## Contributing

 1.  Fork it
 2.  Create a feature branch (`git checkout -b new-feature`)
 3.  Commit changes (`git commit -am "Added new feature xyz"`)
 4.  Push the branch (`git push origin new-feature`)
 5.  Create a new pull request.

## Maintainers

* [Metaleaf.io](http://github.com/MuratSs/)
