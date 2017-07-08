# Simple Style 0.1.0

Welcome! We'd love for you to contribute, and we want you to be you while you do it.

This is a shared project so we need a thin layer of style rules to keep the code easy to use. Just like textbooks use
either Metric or Imperial units, but not both, we need enough consistency that we're not all running around calculating
how many millimeters are in 7/16ths of an inch.

## Principle

Simple Style is about making code usable. Some choices don't effect usability. Here's an example:

    users = [ 'adam', 'robot' ]
    users = ['adam', 'robot']

Those extra spaces are a difference in style but they don't make the code harder or easier to use. When mixing styles
doesn't cause a clear problem, we let the writer choose.

Although `['adam']` and `[ 'adam' ]` don't cause a problem on their own, too much variation eventually gets painful.
Python's PEP8 has some great [examples of where whitespace can go wrong][whitespace]. Imagine if all the spacing
patterns in those examples were present in one project. Try to be consistent.

## Rules

Simple Style's rules are simple because even a thousand style rules will leave a million ways to write gross code. It's
more important to use good judgement than to chase static analysis errors from a thousand rules.

### Languages can be different

Languages can be styled differently within projects. E.g. it's ok to indent with four spaces in Python but only two
in Bash.

### Use consistent indentation

Mixed indentations make it easier to get lost. You'll think you're in a condition when really you're in the loop above
it, etc.

### Use consistent delimiters

If you're looking for Tom Servo it should be obvious whether to search for tom_servo, tomservo, or TomServo.

If you need to parse a list of user names into database fields, would you rather have these:

    tomServo
    crow_t_robot
    BrainGuy

... or these?:

    tom_servo
    crow_t_robot
    brain_guy

It's ok to use different delimiters for different types of things. Classes can be CamelCase and variables can be
snake_case as long as all classes use one and all variables use the other.

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

This is a waste of a line:

```python
# Iterate through users.
for user in logged_in_users:
```

This is indispensable:

```python
CF_STATES = [
    # Copied from: http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-describing-stacks.html#w1ab2c15c17c21c13
    'CREATE_COMPLETE',
    'CREATE_IN_PROGRESS',
    ...
]
```

## Language Rules

Languages have their own rules. Python has the [PEP8][pep8], Ruby
has a [community guide][ruby_style]. Use them if the project uses them.

**Except** the following. Some rules are excessive and we specifically exclude them.

### [PEP8][pep8]'s English style requirements

Programming is a worldwide, multi-lingual practice. English is a big language with a lot of core features and
learning it is hard. Worse than that, written and spoken English are different. Simple Style removes a burden from
non-native speakers by only requiring understandable English, not pretty English.


[whitespace]: https://www.python.org/dev/peps/pep-0008/#whitespace-in-expressions-and-statements
[pep8]: https://www.python.org/dev/peps/pep-0008/
[ruby_style]: https://github.com/bbatsov/ruby-style-guide
