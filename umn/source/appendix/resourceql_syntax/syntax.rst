:original_name: rms_06_0702.html

.. _rms_06_0702:

Syntax
======

Symbol Conventions
------------------

In this section, the words that need to be typed in the original form are capitalized, and the characters that need to be typed in the original form are enclosed in single quotation marks (').

'[x]' indicates that statement 'x' can be used once or not even once.

'(x)' indicates that statement 'x' is a whole. '(x, ...)' indicates that statement 'x' can be used once or multiple times. If statement 'x' is used multiple times, use commas (,) to separate them.

'|' indicates all possible alternatives.

'expression' indicates any expression. Specially, 'bool_expression' indicates any Boolean expression.

'identifier' indicates a valid identifier. An identifier can contain letters, digits, and underscores (_), and cannot start with a digit.

'column_name' indicates a valid field name. It can be 'identifier' or multiple identifiers, for example,'A.id'.

'table_name' indicates a valid table name. In the ResourceQL syntax, 'table_name' must be 'resources'.

A unit enclosed in double quotation marks ("") is considered as a whole. For example, to indicate a column name containing special characters, add double quotation marks ("") before and after the column name.

Basic Query Syntax
------------------

.. code-block::

   [WITH (with_item, ...)]
   SELECT [DISTINCT | ALL] (select_item, ...)
   [FROM (from_item, ...)]
   [WHERE bool_expression]
   [GROUP BY [DISTINCT | ALL] (expression, ...)]
   [HAVING booleanExpression]
   [ORDER BY (expression [ASC | DESC] [NULLS (FIRST | LAST)], ...)]
   [LIMIT number]

The field in 'select_item' can be renamed. Operation can be performed on the field values. 'select_item' supports the query of all fields in a table.

.. code-block::

   select_item = (expression [[AS] column_name_aias]) | *

'from_item' supports the join function and multiple subqueries, and the table name can be renamed.

.. code-block::

   from_item = table_name [[AS] table_name_aias]
             | (from_item join_type from_item [(ON bool_expression) | USING(column_name, ...)])
             | '(' query ')'

'with_item' is used to customize queries to facilitate subsequent invoking.

.. code-block::

   with_item = identifier AS '(' query ')'

For example, to list resources with a quantity greater than 100 in each region, run the following SQL statement:

.. code-block::

   WITH counts AS (
       SELECT region_id, provider, type, count(*) AS number FROM resources
       GROUP BY region_id, provider, type
   ) SELECT * FROM counts WHERE number > 100

Numeric Operation and Boolean Operation
---------------------------------------

ResourceQL supports binary mathematical operations on integers and floating digits. The following operators are supported:``'+,-,*,/,%'``

Values of the same type can be compared. The following comparison operators are supported: <, >, <=, >=, =, <>, !=. Both <> and != indicate not equal. Values are compared in size, and strings are compared in lexicographic order. Values and sets can also be compared. In this case, one from 'ALL \| SOME \| ANY' on the right of the comparison operator is used to specify the comparison range. 'All' indicates that all elements in the set must be met. 'SOME/ANY' indicates that at least one element must be met.

.. code-block::

   expression ('=' | '<>' | '!=' | '<' | '>' | '<=' | '>=')
   expression
   expression ('=' | '<>' | '!=' | '<' | '>' | '<=' | '>=')
   [ALL | SOME | ANY] '(' query ')'

'bool_expression' indicates any Boolean expression. (**True** or **False** is returned after the operation.) 'bool_expression' includes the following syntax:

.. code-block::

   NOT bool_expression
   bool_expression (AND | OR) bool_expression
   expression [NOT] BETWEEN expression AND expression
   expression [NOT] IN '(' query ')'
   EXISTS '(' query ')'
   expression [NOT] LIKE pattern [ESCAPE escape_characters]
   expression IS [NOT] NULL
   expression IS [NOT] DISTINCT FROM expression

In particular, operator '||' concatenates the left and right values and returns a new value. The left and right values are of the same type: array or string.

Timestamp
---------

ResourceQL allows you to query fields of the time type. The query result is converted to the zero time zone and returned in ISO Date format. The result is saved in milliseconds.

Time types can be connected by comparison operators. If you want to use a literal to indicate time, use timestamps to write 'time'. 'time' can be in any ISO date format or a common time format. The following formats are allowed:

2019-06-17T12:55:42.233Z

2019-06-17T12:55:42Z

2019-06-17 12:55:42

2019-06-17T12:55:42.00 + 08:00

2019-06-17 05:55:40 - 06:00

2019-06-17

2019

If the time zone is not added, the zero time zone is used by default. If the 24-hour time is not added, 0:00 is used by default. If the month is not added, January 1 is used by default.

For example, to sort resources created since 12:55:00 on September 12, 2020 by update time in descending order, run the following statement:

.. code-block::

   select name, created, updated from resources
   where created >= timestamp '2020-09-12T12:55:00Z'
   order by updated DESC

Fuzzy Search
------------

.. code-block::

   string LIKE pattern [ESCAPE escape_characters]

'LIKE' is used to determine whether a character string complies with a pattern. If you want to express the literal of '%' and '_' in the pattern, you can specify an escape character (for example, '#') after ESCAPE and write '# %' and '#_' in the pattern.

Wildcard '%' indicates that zero or multiple characters are matched.

Wildcard '_' indicates that one character is matched.

The fuzzy query of OBS buckets can be written in the following format:

.. code-block::

   SELECT name, id FROM resources
       WHERE provider = 'obs' AND type = 'buckets' AND name LIKE '%figure%'

or

.. code-block::

   SELECT name, id FROM resources
       WHERE provider = 'obs' AND type = 'buckets' AND name LIKE '%figure#_%' ESCAPE '#'

Condition Functions
-------------------

The return value of CASE varies according to the actual situation. CASE can be used in either of the following ways:

-  Calculate the value of a given expression and return the corresponding result based on the value.
-  Calculate the value of each bool_expression in sequence, finds the first expression that meets the requirements, and returns the result.

.. code-block::

   CASE expression
       WHEN value1 THEN result1
       [WHEN value2 THEN result2]
       [...]
       [ELSE result]
   END
   CASE
       WHEN condition1 THEN result1
       WHEN condition2 THEN result2
       [...]
       [ELSE result]
   END

**IF** can be used in either of the following ways:

-  'IF(bool_expression, value)': If the bool_expression value is true, 'value' is returned. Otherwise, NULL is returned.
-  'IF(bool_expression, value1, value2)': If the Boolean expression value is true, 'value1' is returned. Otherwise, 'value2' is returned.

Using Functions to Simplify Queries
-----------------------------------

ResourceQL provides a variety of functions to simplify queries. For details about the functions, see :ref:`Functions <rms_06_0703>`.

ResourceQL supports lambda expressions. The arguments of some functions may be another function. In this case, it is convenient to use the lambda expression.

For example, to list the ECSs and the EVS disks attached to each ECS, run the following SQL statement:

.. code-block::

   SELECT ECS.id AS ecs_id, EVS.id AS evs_id FROM
       (SELECT id, transform(properties.ExtVolumesAttached, x -> x.id) AS evs_list
       FROM resources WHERE provider = 'ecs' AND type = 'cloudservers') ECS
       (SELECT id FROM resources WHERE provider = 'evs' AND type = 'volumes') EVS
       WHERE contains(ecs.evs_list, evs.id)

'contains(a, element)→boolean' determines whether an element appears in array a.

'transform(array(T), function(T, S))→array(S) can convert an array of a certain type into an array of another type.

Join and Unnest
---------------

ResourceQL supports 'JOIN' and 'UNNEST'. 'JOIN' can be classified into the following types:

-  [INNER] JOIN
-  LEFT [OUTER] JOIN
-  RIGHT [OUTER] JOIN
-  FULL [OUTER] JOIN

'JOIN' must be followed by 'USING(...)' or 'ON <bool_expression>'.

'USING' is used to specify the names of columns to join.

'ON' accepts a Boolean expression and merges values of 'JOIN' if the Boolean expression value is true. To ensure performance, there must be at least one equation in a Boolean expression in the conjunctive normal form (CNF), and the operation content at the left and right ends of the equation is provided by the left and right tables separately.

You can add 'NATURAL' before 'JOIN' to indicate a connection. In this case, you do not need to add 'USING' or 'ON' after 'JOIN'.

'UNNEST' can unpack an array into a table. With 'WITH ORDINALITY', there is an auto-increment column. The format is as follows:

.. code-block::

   table_name CROSS JOIN UNNEST '(' (expression, ...) ')' [WITH ORDINALITY]

Note that 'CROSS JOIN' can only be used to connect to 'UNNEST'. ResourceQL does not support 'CROSS JOIN' in other formats.

The preceding example of querying the association between an ECS and an EVS disk can also be written in the following format:

.. code-block::

   SELECT ECS_EVS.id AS ecs_id, EVS.id AS evs_id FROM
       (SELECT id, evs_id FROM (SELECT id, transform(properties.ExtVolumesAttached, x ->x.id) AS evs_list
            FROM resources WHERE provider = 'ecs' AND type = 'cloudservers') ECS
        CROSS JOIN UNNEST(evs_list) AS t (evs_id)) ECS_EVS,
        (SELECT id FROM resources WHERE provider = 'evs' AND type = 'volumes') EVS
        WHERE ECS_EVS.evs_id = EVS.id
