This directory contains files that are necessary to make expressions work.
Expressions can be evaluated at runtime (i.e. when playing an Oppia exploration)
and can reference parameters and system variables to produce textual output
(e.g. used in a message presented to users) as well as boolean results which
may be used to control state transitions.
Example string expressions:
- "Hello " + userName + "!"
- "The answer is " + (x + y * z) + "."
Example boolean expressions:
- answer == "yes"
- loopCounter > 100

See comments in parser.pegjs for the description of input expression grammar.
Also see parser.pegjs for the parser output (i.e. parse tree) data format.
See evaluator.js for the operator contracts.

Files:
parser.pegjs
  This is the parser definition which is used to generate the parser.js file
  that will be used at runtime to parse user-entered expressions.
parser.js
  This is the JavaScript parser file produced by PEGJS and the input file
  parser.pegjs.
evaluator.js
  Implementation of the expression evaluator. Includes the evaluation engine
  as well as the system operators.
parserSpec.js
  Tests for the parser.
evaluatorSpec.js
  Tests for the evaluator.

How to update the parser:
1. Modify parser.pegjs.
2. Add tests in test.js for the new or modified grammar.
3. Run

      bash scripts/create_expression_parser.sh

   which updates parser.js. Then run the JS tests using

      bash scripts/run_js_tests.sh

   to ensure that the new grammar passes the tests in parserSpec.js and
   evaluatorSpec.js.
4. Repeat 1-3 until the desired grammar is written and tested.
5. Check the changes. You need to check in parser.pegjs as well as parser.js
  (and probably parserSpec.js and evaluatorSpec.js).
