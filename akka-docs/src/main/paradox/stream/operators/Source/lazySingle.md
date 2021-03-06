# lazySingle

Defers creation of a single element source until there is demand.

@ref[Source operators](../index.md#source-operators)

@@@div { .group-scala }

## Signature

@@signature [Source.scala](/akka-stream/src/main/scala/akka/stream/scaladsl/Source.scala) { #lazySingle }

@@@

## Description

Invokes the user supplied factory when the first downstream demand arrives, then emits the returned single value 
downstream and completes the stream.

Note that asynchronous boundaries (and other operators) in the stream may do pre-fetching which counter acts
the laziness and will trigger the factory immediately.

## Reactive Streams semantics

@@@div { .callout }

**emits** when there is downstream demand and the element factory has completed

**completes** after emitting the single element

@@@

