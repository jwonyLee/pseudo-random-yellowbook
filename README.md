# pseudo-random-yellowbook
A yellow-book of pseudo-random number generation of modern programming languages.

List ordering follows [TIOBE Index](https://www.tiobe.com/tiobe-index/).


| Language | Module | 1 <= integer <= 10 | 0 <= float < 100 |
|----------|--------|--------------------|------------------|
| C | [`stdlib.h`](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/stdlib.h.html) | [`rand() % 10 + 1`](https://www.gnu.org/software/libc/manual/html_node/ISO-Random.html) | `rand() / (float)RAND_MAX * 100` |
| Python | [`random`](https://docs.python.org/3/library/random.html) | [`random.randint(1, 10)`](https://docs.python.org/3/library/random.html#random.randint) | [`random.random() * 100`](https://docs.python.org/3/library/random.html#random.random) |
| Java | [`java.util.Random`](https://docs.oracle.com/en/java/javase/16/docs/api/java.base/java/util/Random.html) | [`new Random().nextInt(10) + 1`](https://docs.oracle.com/en/java/javase/16/docs/api/java.base/java/util/Random.html#nextInt()) | [`new Random().nextFloat() * 100`](https://docs.oracle.com/en/java/javase/16/docs/api/java.base/java/util/Random.html#nextFloat()) |
| C++ | `<random>` | (mt19937...) | |
| C# | [`System`](https://docs.microsoft.com/dotnet/api/system.random)| [`new Random().Next(1, 11)`](https://docs.microsoft.com/en-us/dotnet/api/system.random.next) | [`new Random().NextDouble() * 100`](https://docs.microsoft.com/dotnet/api/system.random.nextdouble) |
| Visual Basic | [`VBMath`](https://docs.microsoft.com/dotnet/api/microsoft.visualbasic.vbmath) | [`CInt(Int((Rnd() * 10) + 1))`](https://docs.microsoft.com/dotnet/api/microsoft.visualbasic.vbmath.rnd) | `Rnd() * 100` |
| JavaScript | [`Math`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math) | [`Math.floor(Math.random() * 10) + 1`](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math/random) | `Math.random() * 100` |
| Assembly |
| PHP | [Math](https://www.php.net/manual/en/book.math.php) (core) | [`mt_rand(1, 10)`](https://www.php.net/manual/function.rand.php) | [`mt_rand() / (float)(mt_getrandmax() + 1) * 100`](https://www.php.net/manual/en/function.mt-getrandmax.php) |
| [SQL](#sql) | - | `SELECT TRUNC(RANDOM() * 10) + 1` | `SELECT RANDOM() * 100` |
| Ruby | [Random](https://ruby-doc.org/core-3.0.2/Random.html) | [`rand(10) + 1`](https://ruby-doc.org/core-3.0.2/Random.html#method-i-rand) | [`rand * 100`](https://ruby-doc.org/core-3.0.2/Random.html#method-i-rand) |
| Go | [`math/rand`](https://pkg.go.dev/math/rand) | [`rand.Intn(10) + 1`](https://pkg.go.dev/math/rand#Intn) | [`rand.Float64() * 100`](https://pkg.go.dev/math/rand#Float64) |
| Swift |
| MATLAB | [intrinsic](https://www.mathworks.com/help/matlab/random-number-generation.html) | [`randi(10)`](https://www.mathworks.com/help/matlab/ref/randi.html) | [`rand * 100.0`](https://www.mathworks.com/help/matlab/ref/rand.html) |
| [Fortran](#fortran) | intrinsic | [`CALL RANDOM_NUMBER(r); i = ceiling(r*10)`](https://gcc.gnu.org/onlinedocs/gfortran/RANDOM_005fNUMBER.html#RANDOM_005fNUMBER) | [`CALL RANDOM_NUMBER(r); r = r*100`](https://gcc.gnu.org/onlinedocs/gfortran/RANDOM_005fNUMBER.html#RANDOM_005fNUMBER) |
| R |
| Perl |
| Delphi |
| Rust |
| Julia | [`Random`](https://docs.julialang.org/en/v1/stdlib/Random) | [`abs(rand(UInt64)) % 10 + 1`](https://docs.julialang.org/en/v1/stdlib/Random/#Base.rand) | [`abs(rand(Float64)) * 100`](https://docs.julialang.org/en/v1/stdlib/Random/#Base.rand)
| Scala | [`scala.util.Random`](https://www.scala-lang.org/api/3.0.2/scala/util/Random.html) | [`Random.nextInt(10) + 1`](https://www.scala-lang.org/api/3.0.2/scala/util/Random.html#nextInt-fffffbe0) | [`Random.between(1f, 100f)`](https://www.scala-lang.org/api/3.0.2/scala/util/Random.html#between-44b) |

## SQL

Random function is not present in ANSI SQL standard and should be specified in accordance with respective implementations.
  - PostgreSQL: [`RANDOM`](https://www.postgresql.org/docs/current/functions-math.html#FUNCTIONS-MATH-RANDOM-TABLE)
  - MySQL: [`RAND`](https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html#function_rand)

## Fortran
* `i` is `INTEGER` and `r` is `REAL`.
* Declare output variable first and pass it to `RANDOM_NUMBER`.
  ```fortran
    PROGRAM test_random_number
        REAL :: r
        CALL RANDOM_NUMBER(r)
    END PROGRAM
  ```
