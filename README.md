# Reproduce wartremover flaw

This project is simply an instantiation of http4s giter8 template with `Warts.unsafe`. Compiling it fails with

```
[error] /Users/joao.fe/workspace/wartremover-issue/quickstart/src/main/scala/com/example/quickstart/Main.scala:12:15: [wartremover:Any] Inferred type containing Any: cats.data.Kleisli[[+A]cats.effect.IO[A],org.http4s.Request[cats.effect.IO],org.http4s.Response[[+A]cats.effect.IO[A]]]
[error]   private val helloWorldService = HttpRoutes
[error]               ^
[error] /Users/joao.fe/workspace/wartremover-issue/quickstart/src/main/scala/com/example/quickstart/Main.scala:13:13: [wartremover:Any] Inferred type containing Any: [+A]cats.effect.IO[A]
[error]     .of[IO] {
[error]             ^
[error] /Users/joao.fe/workspace/wartremover-issue/quickstart/src/main/scala/com/example/quickstart/Main.scala:14:16: [wartremover:Any] Inferred type containing Any: [+A]cats.effect.IO[A]
[error]       case GET -> Root / "hello" / name =>
[error]                ^
[error] /Users/joao.fe/workspace/wartremover-issue/quickstart/src/main/scala/com/example/quickstart/Main.scala:15:11: [wartremover:Any] Inferred type containing Any: [+A]cats.effect.IO[A]
[error]         Ok(s"Hello, $name.")
[error]           ^
[error] /Users/joao.fe/workspace/wartremover-issue/quickstart/src/main/scala/com/example/quickstart/Main.scala:21:15: [wartremover:Any] Inferred type containing Any: [+A]cats.effect.IO[A]
[error]       .default[IO]
[error]               ^
[error] /Users/joao.fe/workspace/wartremover-issue/quickstart/src/main/scala/com/example/quickstart/Main.scala:22:17: [wartremover:OptionPartial] Option#get is disabled - use Option#fold instead
[error]       .withHost(ipv4"0.0.0.0")
[error]                 ^
[error] /Users/joao.fe/workspace/wartremover-issue/quickstart/src/main/scala/com/example/quickstart/Main.scala:23:17: [wartremover:OptionPartial] Option#get is disabled - use Option#fold instead
[error]       .withPort(port"8080")
[error]                 ^
[error] 7 errors found
[error] (Compile / compileIncremental) Compilation failed
```
