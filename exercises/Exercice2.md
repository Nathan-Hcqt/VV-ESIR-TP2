
# Using PMD


Pick a Java project from Github (see the [instructions](../sujet.md) for suggestions). Run PMD on its source code using any ruleset (see the [pmd install instruction](./pmd-help.md)). Describe below an issue found by PMD that you think should be solved (true positive) and include below the changes you would add to the source code. Describe below an issue found by PMD that is not worth solving (false positive). Explain why you would not solve this issue.


## Answer

first error :

pmd error : UnnecessaryFullyQualifiedName:	Unnecessary qualifier 'AccurateMath': 'pow' is already in scope
code line : return AccurateMath.pow(x, (y < 0) ? -l : l);

This error don't need to be solve because it just indicate that the function pow already exist. Here we specify that we use th pow function from AccurateMath so it has no impact.


seconde error : 

pmd error : CloseResource:	Ensure that resources like this PrintStream object are closed after use
code line : PrintStream out = System.out;

This error need to be solve because it uses ressources, the object is not close after use.
In order to solve this we can implement/modify this code : "PrintStream out = System.out;" by this :

    "try (PrintStream out = System.out;) {

    } catch (FileNotFoundException e) {
        e.printStackTrace();
    }"