sbt-avro
========

[![Build Status](https://travis-ci.org/sbt/sbt-avro.svg?branch=master)](https://travis-ci.org/sbt/sbt-avro)

# Overview

[sbt-avro](http://avro.apache.org) is a [sbt](http://www.scala-sbt.org) plugin for generating Java sources for Avro schemas. It also supports referencing schemas from different files.

# Usage

## Installing the plugin

Add the plugin according to the [sbt documentation](https://www.scala-sbt.org/1.x/docs/Using-Plugins.html).

For instance, add the following lines to `project/plugins.sbt`:

```
addSbtPlugin("com.cavorite" % "sbt-avro" % "2.0.0")

// Java sources compiled with one version of Avro might be incompatible with a
// different version of the Avro library. Therefore we specify the compiler
// version here explicitly.
libraryDependencies += "org.apache.avro" % "avro-compiler" % "1.9.2"
```

Add the library dependency to `build.sbt`:

```
// Version must match that of `avro-compiler` in `project/plugins/sbt`
libraryDependencies += "org.apache.avro" % "avro" % "1.9.2"
```

## Settings

| Name                           | Default                           | Description |
|:-------------------------------|:----------------------------------|:------------|
| `avroSource`                   | `sourceDirectory` / `avro`        | Source directory with `*.avsc`, `*.avdl` and `*.avpr` files. |
| `avroGenerated / target`       | `sourceManaged` / `compiled_avro` | Source directory for generated `.java` files. |
| `avroStringType`               | `CharSequence`                    | Type for representing strings. Possible values: `CharSequence`, `String`, `Utf8`. |
| `avroUseNamespace`             | `false`                           | Validate that directory layout reflects namespaces, i.e. `src/main/avro/com/myorg/MyRecord.avsc`. |
| `avroFieldVisibility`          | `public_deprecated`               | Field Visibility for the properties. Possible values: `private`, `public`, `public_deprecated`. |
| `avroEnableDecimalLogicalType` | `true`                            | Set to true to use `java.math.BigDecimal` instead of `java.nio.ByteBuffer` for logical type `decimal`. |

## Examples

For example, to change the Java type of the string fields, add the following lines to `build.sbt`:

```
avroStringType := "String"
```

## Tasks

| Name           | Description |
|:---------------|:------------|
| `avroGenerate` | Generate Java sources for Avro schemas. This task is automatically executed before `compile`.

# License
This program is distributed under the BSD license. See the file `LICENSE` for more details.

# Credits

`sbt-avro` is maintained by the [sbt Community](http://www.scala-sbt.org/release/docs/Community-Plugins.html). The initial code was based on a similar plugin: [`sbt-protobuf`](https://github.com/gseitz/sbt-protobuf). Feel free to file issues or pull requests.

# Contributors

- [Juan Manuel Caicedo](https://cavorite.com)
- [Brennan Saeta](https://github.com/saeta)
- [Daniel Lundin](https://github.com/dln)
- [Vince Tse](https://github.com/vtonehundred)
- [Ashwanth Kumar](https://github.com/ashwanthkumar)
- [Jérôme Wacongne](https://github.com/ch4mpy)
- [Ben McCann](http://www.benmccann.com)
- [Ryan Koval](https://github.com/rkoval)
- [Saket Kumar](https://github.com/skate056)
- [Julian Peeters](https://github.com/julianpeeters)
- [Przemysław Dubaniewicz](https://github.com/przemekd)
- [Neville Li](https://github.com/nevillelyh)
- [Michel Davit](https://github.com/RustedBones)
