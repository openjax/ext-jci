# OpenJAX Extensions JCI

> Java API Extension for the Java Compiler Interface

[![Build Status](https://travis-ci.org/openjax/ext-jci.png)](https://travis-ci.org/openjax/ext-jci)
[![Coverage Status](https://coveralls.io/repos/github/openjax/ext-jci/badge.svg)](https://coveralls.io/github/openjax/ext-jci)
[![Javadocs](https://www.javadoc.io/badge/org.openjax.ext/jci.svg)](https://www.javadoc.io/doc/org.openjax.ext/jci)
[![Released Version](https://img.shields.io/maven-central/v/org.openjax.ext/jci.svg)](https://mvnrepository.com/artifact/org.openjax.ext/jci)

## Introduction

Java's tools API provides an abstract interface for the implementation of runtime compilers. Though this interface provides the full span of functionality necessary to compile Java source in runtime, the APIs fall short to provide a reference implementation to allow developers to easily integrate a runtime compiler into their applications.

OpenJAX Extensions JCI provides a reference implementation of Java's runtime compiler API with its `InMemoryCompiler`, which can be used to compile sources and load the resulting bytecode in runtime.

## Usage

  The following example illustrates how to compile Java source into bytecode that is thereafter available to be loaded in the resulting `ClassLoader`.

  ```java
    final InMemoryCompiler compiler = new InMemoryCompiler();
    compiler.addSource("public class HelloWorld {public String helloWorld() {return \"Hello world!\";}}");
    final ClassLoader classLoader = compiler.compile();

    final Class<?> cls = classLoader.loadClass("HelloWorld");
    final Object obj = cls.getConstructor().newInstance();
    assertEquals("helloWorld", cls.getMethod("helloWorld").invoke(obj));
  ```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

### License

This project is licensed under the MIT License - see the [LICENSE.txt](LICENSE.txt) file for details.