# Example Usage

## Try It Now -- Sample Project

A sample project with deliberately mixed-quality tests is included at `examples/sample-project/`. This is the fastest way to see the plugin in action.

### Quick start

```bash
# 1. Copy the sample project somewhere
cp -r /path/to/farley_score/examples/sample-project /tmp/sample-project

# 2. Install the plugin into it
/path/to/farley_score/setup-project.sh /tmp/sample-project

# 3. Launch Claude Code
cd /tmp/sample-project
claude
```

Then inside Claude Code:

```
/msec:farley-score tests/
```

### What's in the sample project?

The sample includes 21 test methods across 2 files, deliberately designed with a mix of quality:

**Good tests** (7 methods):
- Behavior-driven names (`test_should_add_two_positive_numbers`)
- Single assertion per test
- Proper mock usage (testing real classes with mock collaborators)

**Bad tests** (14 methods) covering every anti-pattern:
- Trivial tautologies (`assertTrue(True)`, `assertEqual(1, 1)`)
- Mock tautologies (assert mock returns configured value)
- Mock-only tests (no production code exercised)
- Framework tests (testing Python's `+` operator)
- Mega-test (6 assertions in one test)
- Shared mutable state (class-level `shared_calc`)
- `time.sleep()` call
- Private attribute access (`calc._history`)
- Over-specified interactions (call count + ordering)
- Cryptic test name (`test_it_works`)

**Expected Farley Index: ~5.7 (Fair)**

---

## Autonomous Review

### Basic usage
```
/msec:farley-score tests/
```

### Specify a subdirectory
```
/msec:farley-score src/test/java/com/myapp/
```

### Natural language
```
/msec:farley-score evaluate test quality for the whole project
```

---

## Interactive Coaching

### Start a coaching session
```
/msec:farley-score-coach
```

### Focus on a specific property
```
/msec:farley-score-coach help me understand test maintainability
```

### Example Coaching Dialogue

```
Coach: Let's look at this test together:

    def test_user_creation(self):
        user = User("alice", "alice@test.com")
        self.assertEqual(user._name, "alice")
        self.assertEqual(user._email, "alice@test.com")

Which of the 8 properties might this test violate, and why?

You: Maintainable? It's accessing private attributes.

Coach: Exactly! This test is coupled to internal implementation.
If the class renames _name to _username, this test breaks even
though the behavior hasn't changed.

How would you rewrite it to test behavior instead of implementation?
```
