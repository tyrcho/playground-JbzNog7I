# Welcome!

This Kotlin template lets you get started quickly with a simple one-page playground.

```kotlin runnable
fun <T> ((T) -> Boolean).not(): (T) -> Boolean = { !this(it) }

fun main(args: Array<String>) {
    val isOne: (Int) -> Boolean = { it == 1 }
    // use it like this
    val isNotOne = isOne.not()

    println(isOne(1))
    println(isOne(2))
    println(isNotOne(1))
    println(isNotOne(2))
    
    val isAValidRef: String.() -> Boolean = { startsWith("ref-") }
    
    // not like this
    println(if(isAValidRef("ref-12345")) "ok" else "ko")
    
    // but like this
    println(if("ref-12345".isAValidRef()) "ok" else "ko")
    
    // or even better
    fun String.isAValidRefFun() = startsWith("ref-")
    println(if("ref-12345".isAValidRefFun()) "ok" else "ko")
}
```
