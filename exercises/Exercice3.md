# Extending PMD

Use XPath to define a new rule for PMD to prevent complex code. The rule should detect the use of three or more nested `if` statements in Java programs so it can detect patterns like the following:

```Java
if (...) {
    ...
    if (...) {
        ...
        if (...) {
            ....
        }
    }

}
```
Notice that the nested `if`s may not be direct children of the outer `if`s. They may be written, for example, inside a `for` loop or any other statement.
Write below the XML definition of your rule.

You can find more information on extending PMD in the following link: https://pmd.github.io/latest/pmd_userdocs_extending_writing_rules_intro.html, as well as help for using `pmd-designer` [here](./designer-help.md).

Use your rule with different projects and describe you findings below. See the [instructions](../sujet.md) for suggestions on the projects to use.

## Answer

 <ruleset name="Custom Rules"
         xmlns="http://pmd.sourceforge.net/ruleset/2.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://pmd.sourceforge.net/ruleset/2.0.0 http://pmd.sourceforge.net/ruleset_2_0_0.xsd"
         xmlns:pmd="http://pmd.sourceforge.net/ruleset/2.0.0">

    <description>
        Custom ruleset to detect deeply nested if statements.
    </description>

    <rule name="AvoidDeeplyNestedIfStatements"
          language="java"
          class="net.sourceforge.pmd.lang.rule.xpath.XPathRule"
          message="Avoid using three or more nested if statements."
          severity="3">
        
        <description>
            This rule detects three or more nested if statements. Deeply nested if statements can reduce code readability and should be refactored.
        </description>

        <properties>
            <property name="xpath">
                <value>
                    //IfStatement[descendant::IfStatement/descendant::IfStatement]
                </value>
            </property>
        </properties>
        
    </rule>
</ruleset>

With this rule, it detect 220 triple if statement in commons-math.