# Simple Style

Welcome! We'd love for you to contribute, and we want you to be you while you do it.

We need some style rules to keep our code easy to use. Just like textbooks use either Metric or Imperial units, but not both, we need enough structure that we don't all run around calculating how many millimeters are in 7/16ths of an inch.

## The Principle

Simple Style is about making code usable. Some choices don't effect usability. Here's an example:

```
users = [ 'adam', 'robot' ]
users = ['adam', 'robot']
```

Those extra spaces are a difference in style but they don't make the code harder or easier to use. When mixing styles doesn't cause a clear problem, we let the writer choose.

Although `['adam']` and `[ 'adam' ]` don't cause a problem on their own, too much variation eventually gets painful. Python's PEP8 has some great [examples of where whitespace can go wrong][whitespace]. Imagine if all the spacing patterns in those examples were present in one project. Try to be consistent.

## Our Rules

Simple Style's rules are simple because even a thousand style rules will leave a million ways to write gross code. It's more important to use good judgement than to chase static analysis errors from a thousand rules.

### Languages can be different

Languages can be styled differently within projects. E.g. it's ok to indent with four spaces in Python but only two in Bash.

### Use consistent indentation

Mixed indentations make it easier to get lost.

If you glance too quickly at this JSON object, it might look like there's a person called "robots":

```javascript
{
    "people": [
        "adam",
        "bob"
    ],
        "robots": [
        "tom_servo",
        "crow_t_robot"
    ]
}
```

If we make the indentation consistent, it's easy to see that "robots" is actually another array:

```javascript
{
    "people": [
        "adam",
        "bob"
    ],
    "robots": [
        "tom_servo",
        "crow_t_robot"
    ]
}
```

The problem is small in a made-up example like this, but it grows with the size of your code. Once you're looking at five screens of text, it's a lot easier to get lost.

Mixed indentations are worst when they happen inside of one file, but they cause similar problems across files. If half your JSON is indented with two space and the other half is indented with four, it's harder to compare them. Try to be consistent everywhere.

### Use consistent delimiters

If you're looking for Tom Servo it should be obvious whether to search for tom_servo, tomservo, or TomServo.

If you need to parse a list of user names into database fields, would you rather have these:

```
tomServo
crow_t_robot
BrainGuy
```

... or these?:

```
tom_servo
crow_t_robot
brain_guy
```

It's ok to use different delimiters for different types of things. Classes can be CamelCase and variables can be snake_case as long as all classes use one and all variables use the other.

### Refactor names until they're clear

Not great:

```python
for i in sessions:  # Session objects? Users with sessions?
    ...
    i.logout()  # What was 'i', again?
```

Awesome:

```python
for user in logged_in_users:
    ...
    user.logout()
```

### Add comments to explain what the code can't

This wastes a line:

```python
# Iterate through users.
for user in logged_in_users:
```

This is indispensable:

```python
CLOUDFORMATION_STATES = [
    # Copied from: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-describing-stacks.html#w2ab1c15c15c17c11
    'CREATE_COMPLETE',
    'CREATE_IN_PROGRESS',
    ...
]
```

If you feel the code is hard to understand without a comment to explain it, consider revising the code before judging that you've found an exception to Simple Style's rules.

## Language-Specific Styles

Languages and the communities around them sometimes have established styles. Python has the [PEP8][pep8], Ruby has a [community guide][ruby_style]. The patterns they define can make consistency easy. If their styles work for you, use them!


[pep8]: https://www.python.org/dev/peps/pep-0008/
[pep8_english]: https://www.python.org/dev/peps/pep-0008/#comments
[ruby_style]: https://github.com/bbatsov/ruby-style-guide
[whitespace]: https://www.python.org/dev/peps/pep-0008/#whitespace-in-expressions-and-statements
