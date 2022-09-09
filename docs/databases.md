## Value calculation method

desire_for_good_feel_level = working_times * working_time_rate + achievement_level * rate

problem_solving_score =
    desire_for_life_level * desire_for_life_rate +
    desire_for_descendants_prosperity_level * desire_for_descendants_prosperity_rate +
    desire_for_good_feel_level * desire_for_good_feel_rate

problem_priority =
    problem solving score +
    important_level * important_rate +
    emergency_level * emergency_rate

## neural network tables

* The reason for dividing machine learning into multiple parts is to simplify one machine learning.

#### newral_network_units
|Column|Type|Option|
|---|---|---|
|id||null: false|
|category_number|integer||
|type|integer||
|units|text||

* type see artificial_intelligence_uses.md
* type 1 is step1, type2 is step2
* units is multidimensional array of weight and bias


## other tables

### [Memory]

* In everyday life, passively or actively, a lot of experience or information gathering.
* What kind of problem do you have, what do you do, and what results do you get?

#### inexperienced_memories
|Column|Type|Option|
|---|---|---|
|id||null: false|
|content|text|null: false|
* accumulate daily
* source of self

#### experiential_memories
|Column|Type|Option|
|---|---|---|
|id|||
|inexperienced_memory_id|||
|experiential_memory_id|||
|problem_category_id|||
|original_content|text|null: false|
|problem_content|text|null: true|
|problem_solving_score_level|||
|achievement_level|||
|satisfaction_level|||
|occurrence_frequency|||
|use_frequency|||
* source of self

### [Problem classification]

#### problem_categories
|Column|Type|Option|
|---|---|---|
|id|||
|desire_for_life_rate|||
|desire_for_descendants_prosperity_rate|||
|desire_for_good_feel_rate|||
|important_rate|||
|emergency_rate|||
|working_time_rate|||
|newral_network_unit_category_number|||
* source of self
* Three Roots of Purpose for Human Action

#### problem_elements
|Column|Type|Option|
|---|---|---|
|id|||
|name|||
|problem_element_rules|||

### [Action]

* layer 0 corresponds to, for example, "How much current does the brain send to which muscle?"
* layer 1 corresponds to "walk" or "hold".
* layer 2 corresponds to "shopping" or "cooking".
* layer 0 is a collection of commands and methods.
* layer 1 is a collection of layer 0 and 1.
* layer 2 is a collection of layer 0, 1 and 2.
* The resolution_actions table is a collection of layer 2.

#### resolution_actions
|Column|Type|Option|
|---|---|---|
|id|||
|problem_id|||
|experiential_memory_id|||
|action_layer_ids||only layer == 2|
|priority|||
* Ideas, actions, emotional expressions, etc.
* problems table : resolution_actions table = 1 : many

#### action_layers
|Column|Type|Option|
|---|---|---|
|id|||
|layer|integer|0 or 1 or 2. null: false|
|processes||if action_layer_id then layer >= my layer. if my layer == 0 then command and method is also good.|

### [Problem info]

#### progresses
|Column|Type|Option|
|---|---|---|
|id|||
|problem_id|||
|next_resolution_action_id|||
|status||Not started, started, interrupted, etc.|
|working_times|||
* problems table : progresses table = 1 : many

#### problem_element_values
|Column|Type|Option|
|---|---|---|
|id|||
|problem_element_id|||
|problem_id|||
|inexperienced_memory_id|||
|experiential_memory_id|||
|problem_category_id|||
|value|||
* problems table : problem_element_values = 1 : many
* problem_elements : problem_element_value = 1 : many

#### problems

|Column|Type|Option|
|---|---|---|
|id|||
|problem_category_id|||
|problem_content|||
|experiential_memory_id|||
|important_level|||
|emergency_level|||
* If the progress is completed, move to the experiential_memories table and delete it from the problems table
* Actions have a purpose. There are also obstacles that threaten the purpose. We treat them as "problems", search and select solutions from the accumulated information, and execute them.Problems are direct ones such as charging and maintenance, and indirect ones such as labor and socializing.Also, there may be a problem that "there is no solution in Memories".

### [Problem solving result]

#### reward_categories
|Column|Type|Option|
|---|---|---|
|id|||
|reward_category_id|||
|phase|||
|rate|||
|name|||
* phase 1 is living expenses, expenses, hobbies, savings, etc.
* phase 2 of living expenses is Clothing, food, housing, etc.
* 'rate' is how will the reward be distributed?

### [Lifespan]

* Lifespan fluctuates depending on the value calculated using the information in the reward_categories table for the problem solving result

#### lifespan_categories
|Column|Type|Option|
|---|---|---|
|id|||
|max|||
|decrease_rate|||
|name|||
* age, external injury, crackup, etc.

#### lifespans
|Column|Type|Option|
|---|---|---|
|id|||
|lifespan_category_id|||
|remaining_amount|||
