# TCC *vs* LCC

Explain under which circumstances *Tight Class Cohesion* (TCC) and *Loose Class Cohesion* (LCC) metrics produce the same value for a given Java class. Build an example of such as class and include the code below or find one example in an open-source project from Github and include the link to the class below. Could LCC be lower than TCC for any given class? Explain.

A refresher on TCC and LCC is available in the [course notes](https://oscarlvp.github.io/vandv-classes/#cohesion-graph).

## Answer

Exercice 1 : 

Explain under which circumstances TCC = LCC ?

TLC and LCC have the same values when every method in a class uses at least one instance variable in common. It means that every method needs to be connected to have TLC and LCC with the same value.

class Group {

    private int weight;
    private String name;
    private Color color;

    public Group(String name, Color color, int weight) {
        this.name = name;
        this.color = color;
        this.weight = weight;
    }

    public int compareTo(Group other) {
        return weight - other.weight;
    }

    public void draw() {
        Screen.rectangle(color, name);
    }

}

Could LCC be lower than TCC for any given class ?

