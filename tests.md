==On not writing tests

Automated testing is important.  OK?  Now that we got that out of the way, let's look at some test-writing policies you may want to adopt if you feel you're writing too many tests.

*Test-driven development without tests.* Same as traditional TDD, only you don't write tests.  The important thing is, if think about how would you wrote a test before writing the code, it will shape the way you write the code.  The code will be more modular, less coupled.  It will be much easier to add test later than if you don't even think in TDD fashion.

*Test-driven refactoring.* Don't spend too much time writing tests before hand, but always write tests for the code you're about to refactor. If you don't know enough about the invariants that these tests should preserve, you're probably not ready for refactoring. Research the code.

*Skip unit tests.* Only write acceptance and integration tests. Don't worry (too much) about unit tests: if your code passes integration tests, it works OK from the outside, and that's what matters most.

*Adopt a paradigm and stick to it.* Many languages happily let you to shoot yourself 

*Use a statically-typed language.* It's not about Being able to encode invariants into the t

*Random values test for RDBMS access code.* The test code executes a function to be tested with random arguments (of the correct types). If the function does not return error or throws an exception or whatever -- the test passes. Writing such tests may be easily automated, and you don't even have to think of actual and expected outcomes for different argument sets. The only problem is that such tests don't test much. If the tested function uses its arguments to construct and execute an SQL query, and the query does not match the schema, your DBMS will detect it. 
