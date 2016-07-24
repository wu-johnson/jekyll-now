## 1. Protocol Buffers
1. provides a compiler and a set of libraries that a developer can use to serialize data
2. developer defines the structure or schema of a dataset in a file and compiles is with the Protocol Buffers compiler, which generates the code that can then be used to easily read or write that data
3. support language: c++, java, and python, primarily a data serialization format, can be used for defining remote services


## 2. SequenceFile
1. SequenceFile is a binary flat file format for storing key-value pairs.
2. 3 different formats: uncompressed, record compressed, and block compressed, in record compressed, only the value in a record is compressed. whereas in a block compressed sequencefile, both keys and values are compressed


## 3. columnar storage
1. row-oriented storage is ideal for applications that mostly perform CRUD(create, read, update, delete) operations on data.
2. row-oriented storage is not efficent for analytics applications
3. row-oriented storae cannot be efficently compressed.

## 4. RCFile
1. RCFile first splits a table into row groups, and then stores each row group in column format.

## 5. functional programming
1. functional programming provides a tremendous boost in developer productivity.
2. functional programming makes it easier to write concurrent or multithreaded applications
3. functional programming helps to write robust code.
4. functional programming helps to write elegant code.


## 6. scala language
#### 6.1 Variables
1. mutable variables, declared using keyword var
2. immutable variables, declared using keyword val

#### 6.2 functions
1. function defined using keyword def
2. scala function example

```java
def add(firstInput: Int, secondInput: Int): Int = {
  val sum = firstInput + secondInput
  return sum
}

//example 2
def add(firstInput: int, secondInput: Int) = firstInput + secondInput
```

#### 6.3 methods
1. a method is a function that a member of an object. It defined like and works the same as a function. the only difference is that a method has access to all the fields of the object to which is belongs.

#### 6.4 local functions
1. a function defined inside another function or method is called local function.

#### 6.5 higher-order methods
1. a method that takes a function as an input parameter is called higher-order method.

```java
//example
def encode(n: Int, f: (Int) => Long): Long = {
  val x = n * 10
  f(x)
}
```

#### 6.6 function literals
1. a function literal is an unnamed or anonymous function in source code. It can be used in an application just like a string literl. It can be passed as an input to a higher-order function method or function. It can also be assigned to a variable.

2. a function literal is defined with input parameters in parenthesis, followed by a right arrow and the body of the function.
```java
//example code.
(x: Int) => {
  x + 100
}

//exmaple code
val code = encode(10, (x: Int) => x + 100)
```
#### 6.7 closures
1. the body of a function literals typically uses only input parameters and local variables defined within the function literal.

```java
//好难懂
//例如encodedWithSeed(3,4), 先执行 y = 3 + 1000, 在执行(1003*4) 返回
def encodedWithSeed(num: Int, seed: int): Long = {
  def encode(x: Int, func: (Int) => Long): Long = {
    val y = x + 1000
    func(y)
  }
  val result = encode(num, (n: Int) => (n * seed))
  result
}
```

#### 6.8 classes
1. consists of fields and methods.
2. a class is a template or blueprint for creating objects at runtime.
3. an object is an instance of a class.
4. a class is defined in source code, whereas an object exists at runtime.

```java
//example code.
class Car(mk: String, ml: String, cr: String) {
  val make = ml
  val model = ml
  val color = cl

  def repaint(newColor: String) = {
    color = newColor
  }
}

```

#### 6.9 singletons
1. a class that can be instantiated only once is called singleton.
2. scala provides the keyword object for defining a singleton class.

```java
//exmaple code.
object DatabaseConnection {
  def open(name: String): Int = {

  }

  def read(streamId: Int): Array[Byte] = {

  }
  def close(): Unit = {

  }
}

```


#### 6.10 case class
1. it creates a factory method with the same name.
2. write an instance of a case class without using new.
3. all input parameters specified in the definition of a case class implicityly get a val prefix.

#### 6.11 pattern match
1. replace multi-level if-else sttement.

```java
def colorToNumber(color: String): Int = {
  val num = color match {
    case "Red" => 1
    case "Blue" => 2
    case "Green" => 3
    case "Yellow" => 4
    case _ => 0
  }
  num
}

```

#### 6.12 traits
1. a trait reprenets an interface supported by a hierarchy of related class.
2. a trait looks similar to an abstract class. Both can contain fields and methods.
3. the key difference is that a class can inherit from only on class, but it can inherit from any number of traits.

```java
//example code.
trait Shape {
    def area(): Int
  }

  class Square(length: Int) extends Shape {
    def area = length * length
  }

  class Rectangle(length: Int, width: Int) extends Shape {
    def area = length * width
  }
```

#### 6.13 tuples
1. a tuple is a container for string two or more elements of different types. It is immutable, it cannot be modified after is has been created.
2. is useful in situations where you want to group non-related elements.

```java
val twoElements = ("10", true)
```


#### 6.14 option type
1. an option is a data type indicates the presence or absence of some data.
2. option data type is used with a function or a method that optionally returns a value.
3. it returns either Some(x), where x is the actual returned value, or the None object

```java
//example code
def colorCode(color: String): Option[Int] = {
  color match {
    case "red" => Some(1)
    case "blue" => Some(2)
    case "black" => Some(3)
    case _ => None
  }
}
val code = colorCode("orange")
code match {
  case Some(c) => println("code for orange is: " + c)
  case None => println("code not defined for orange")
}
```

#### 6.15 List
1. List is a linear sequence of elements of the same type.
2. Although an element in a list can be accessed by its index, it is not an efficent data structure for acccessing eleemnts by their indices.

```java
//exmaple code
val xs = List(10,20,30,40)
```

#### 6.16 Higher-order methods on collection classes
##### 1. map

```java
//example code
val xs = List(1,2,3,4)
val ys = xs.map((x: Int) => x * 10)
```

##### 2. flatMap
1. the flat map is similar to map
2. it takes a function as input, applies to each element in a collection, and returns another collection as a result.

##### 3. reduce
1. the reduce method returns a single value. as name implies, it reduces a collection to a single value.
2. the input function to the reduce takes two inputs at a time and returns one value.
3. the input function is a binary operator that must be both associative and commutative.

```java
//example code.

val xsForReduce = List(2,4,6,8,10)
val sum = xsForReduce.reduce((x, y) => x + y)
val product = xsForReduce.reduce((x, y) => x * y)
val max = xsForReduce.reduce((x,y) => if (x > y) x else y)
val min = xsForReduce.reduce((x,y) => if (x < y) x else y)
```
## 7. spark
#### 7.1 spark is fast
1. spark allows in-memory cluster computing.
2. spark has an advanced job execution engine.
#### 7.2 workers
1. a worker provides CPU, memory, and storage resource to spark application.
2. the workers run a Spark application as distributed processes on a cluster of nodes.

#### 7.3 cluster mangers
1. manages computing resources across a cluster of worker nodes.
2. provides low-level scheduling of cluster resources accorss applications.
3. enables multiple applications to share cluster resources and run on the same worker nodes.
4. spark currently supports 3 managers: standalone, Mesos and YARN. Mesos and YARN allow run spark and hadoop applications on the same worker nodes.

#### 7.4 executors
1. an executor is a JVM process that spark creates on each worker for an application.
2. it executes application code concurrently in multiple threads.

#### 7.5 tasks
1. a task is the smallest unit of work that spark sends to executor.
2. executed by a thread in executor on a worker node.
3. each task either return a result to a driver programe or patition its output for shuffle
4. spark creates task for data partition

#### 7.6 application execution  
1. shuffle. A shuffle redistributes data among a cluster of nodes. it is expensive because it involves moving data across a network. Notes: shuffle dose not randomly redistribute data, it groups data elements into buckets bases on some criteria.

2. Job. A job is a set of computations that spark performs to return results to a driver program.

3. Stage. A stage is a collection of tasks. spark splits a job into DAG stages.

## 8. RDD operations
#### 8.1 zip
1. takes an RDD as input and returns an RDD of pairs. where the first element in a pair is from the source RDD and the second element is from the input RDD.

#### 8.2 pipe
1. allows execute an external program in a forked program

#### 8.3 coalesce
1. reduce the number of partitions of an RDD

```java
//example code
val numbers = sc.parallelize((1 to 100).toList)
val numbersWithOneRDD = numbers.coalesce(1)
```

#### 8.4 repartition
