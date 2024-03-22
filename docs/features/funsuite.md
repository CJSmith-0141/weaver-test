Pure tests
==========

If your tests do not require any capability provided by effect-types, you can use a simplified interface `FunSuite`,
which comes with a single `test` method and does not allow effectful tests.

Tests in `FunSuite` are executed sequentially and without the performance overhead of effect
management.


```scala mdoc
object CatsFunSuite extends weaver.FunSuite {
  test("asserts") { expect(Some(5).contains(5)) }

  test("fails")   { expect(Some(25).contains(5)) }

  test("throws")  { throw new RuntimeException("oops") }
}
```

```scala mdoc:passthrough
println(weaver.docs.Output.runSuites(CatsFunSuite))
```
