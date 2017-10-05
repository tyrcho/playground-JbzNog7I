# Welcome!

This Kotlin template lets you get started quickly with a simple one-page playground.

```kotlin runnable
fun <T> ((T) -> Boolean).not(): (T) -> Boolean = { !this(it) }

fun main(args: Array<String>) {
    // Example 1
    val isOne: (Int) -> Boolean = { it == 1 }
    val isNotOne = isOne.not()

    println(isOne(1))
    println(isOne(2))
    println(isNotOne(1))
    println(isNotOne(2))
    
    
    // Example 2
    val isAValidRef: String.() -> Boolean = { startsWith("ref-") }
    
    // not like this
    println(if(isAValidRef("ref-12345")) "ok" else "ko")
    
    // but like this
    println(if("ref-12345".isAValidRef()) "ok" else "ko")
    
    // I think this is an even better version
    fun String.isAValidRefFun() = startsWith("ref-")
    println(if("ref-12345".isAValidRefFun()) "ok" else "ko")
    
    val startWithRef: (String) -> Boolean = {it.startsWith("ref")}
    val endWithBar: (String) -> Boolean = { it.endsWith("bar") }
    
    
    // Example 3
    // Let's go crazy
    // Here we have two implicit receiver
    //              the first one                           and the second one
    //            vvvvvvvvvvvvvvvvv                             vv
    infix fun <T> ((T) -> Boolean).and(other: (T) -> Boolean) : T.() -> Boolean = { this@and(this) && other(this) }
    //             ^^^^^^^*^^^^^^^                              ^                   ^^^^*^^^ ^^^^           ^^^^
    //                    *                                     |-----------------------+------|--------------|
    //                    *                                                             *
    //                    *~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*       
    
    val isValidRef2 = startWithRef and endWithBar
    println("ref-foobar".isValidRef2())
    println("hi mom!".isValidRef2())
}
```
