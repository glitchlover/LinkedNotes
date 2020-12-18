	#Note-mermaid

# Mermaid —————————————————
## Graph  Diagram ---

### Simple Start 👾——————————————

```mermaid
graph TD
	stop --> start
	start --> stop
	A_node!
```

### Nodes and Shapes ———————————–

```mermaid
graph LR
	id1[this is the text in the box]
	id2(this is the tect in the rounded box)
	id3((this is a circle))
	id4>this is a flag]
	id5{this is a rumbus}
	id6{{this is a hexagon}}
	id7[\this is a parallelogram\]
	id8[/this is another parallelogram but is doesn't work/]
	id8[this is a trapezoid]
```

### Links between nodes

```mermaid
	graph TD
	a -->b
	a2 --- b2
		a3 -- text-->b3
	a4 -->|text|b4
	a5 -.-b5
	a6 -.text.-b6
	a7 === b7
	a8 ==> b8
	a9== text ==>b9
```

### Subgraph

```mermaid
graph TD
	subgraph two
	c1 --> a2
	subgraph one
	a1 --> c2
	end
	end
	
```

## Sequence Diagram

### Simple Start

```mermaid
sequenceDiagram
	Alice->>John: how are you?
```

### Participants

```mermaid
sequenceDiagram
	participant alice
```

### Lines and Arrows

| # **Type** | # **Description**                      |
| ---------- | -------------------------------------- |
| =>         | solid line without Arrow               |
| –>         | Dotted line without arrow              |
| –>>        | Solid line with a  arrow head          |
| -x         | Solid line with a cross at the the end |
| –X         | Dotted line with a cross at the end    |



## Class Diagram
### Simple start
```mermaid
classDiagram
	class Animal
	Animal: int age
	Animal: int type
	Animal: isMammal()