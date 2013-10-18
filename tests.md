==On not writing tests

Let's get it out of the way: automated testing is important.  If you're developing a nuclear station control system, or a Mars rover software, you'll definitely have to support a comprehensive test suite.  If you're working on a personal pet project -- at early stages you might get by without any tests at all.  And then there's all the other kinds of software in between, which probably make up most of the software in the world, and which should be covered with tests, to some degree.

Writing tests usually involves trade-off: you spend less time writing production code and more time designing, writting and supporting test code.  Assume there's a deadline or something, and you feel you could do with writing a bit less tests than you do now. Or maybe you don't, but you just inherited a large legacy code base with only a modest amount of tests, and can't afford to stop ongoing development for months just to add test code. 

What policies you can follow to write less tests and get away with it?

(TODO add disclaimer that this is not an endorsement of writing untested code, but a rough guide for surviving the less fortunate real-world projects.)

*Test-driven development without tests.* Same as traditional TDD, only you don't write tests. The important thing is, if think about how would you wrote a test before writing the code, it will shape the way you write the code. The code will be testable by design. More modular, less coupled.  It will be much easier to add test later if you think about it than if you don't even think in TDD fashion.

*Test-driven refactoring.* Don't spend too much time writing tests before hand, but always write tests for the code you're about to refactor. If you don't know enough about the invariants that these tests should preserve, you're probably not ready for refactoring. Research the code you're working on.

*Skip unit tests.* Only write acceptance and integration tests. Don't worry (too much) about unit tests: if your code passes integration tests, it works OK from the outside, and that's what matters most.

*Use safe subset of a language.* Adopt a paradigm or a set or rules and code conventions and stick to it.  Many languages will happily let you to shoot yourself in the foot. One way to mitigate this danger is to limit yourself to a "safe" subset of a language. E.g., if you're using C++, develop a policy of using smart pointers almost everywhere. Or adopt a functional programming style and avoid mutable shared state. 

*Use a statically-typed language.* Types let you specify certain invariants and check and enforce them at compile-time. The more compiler can infer and check from the metadata in the code, the less you have to check yourself. This is actually a more general point, not limited to type systems. Other static verification techniques will also do, provided they don't add too much coding overhead.

*Random values test for RDBMS access code.* The test code executes a function to be tested with random arguments (of the correct types). If the function does not return error or throws an exception or whatever -- the test passes. Writing such tests may be easily automated, and you don't even have to think of actual and expected outcomes for different argument sets. The only problem is that such tests don't test much. If the tested function uses its arguments to construct and execute an SQL query, and the query does not match the schema, your DBMS will detect it. 
