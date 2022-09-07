## tables

### [Memory]

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
|original_content|text|null: false|
|problem_content|text|null: true|
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
|important_level|||
|emergency_level|||
* source of self

#### problem_elements
|Column|Type|Option|
|---|---|---|
|id|||
|name|||
|problem_element_rules|||

### [Action]

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
