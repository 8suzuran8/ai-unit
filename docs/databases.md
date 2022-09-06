## tables

### [Memory]

#### inexperienced_memories
|Column|Type|Option|
|---|---|---|
|id||null: false|
|content|text|null: false|

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

### [Problem classification]

#### problem_categories
|Column|Type|Option|
|---|---|---|
|id|||
|problem_solving_score_rate|||
|important_level|||
|emergency_level|||

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
|action_layer_ids||only layer == 3|
|priority|||

#### action_layers
|Column|Type|Option|
|---|---|---|
|id|||
|layer|integer|null: false|
|processes||if action_layer_id then layer >= my layer. if my layer == 0 then command and method is also good.|

### [Problem info]

#### progresses
|Column|Type|Option|
|---|---|---|
|id|||
|problem_id|||
|next_resolution_action_id|||
|status|||
|working_times|||

#### problem_element_value
|Column|Type|Option|
|---|---|---|
|id|||
|problem_element_id|||
|problem_id|||
|inexperienced_memory_id|||
|experiential_memory_id|||
|problem_category_id|||
|value|||

#### problems
|Column|Type|Option|
|---|---|---|
|id|||
|problem_category_id|||
|problem_content|||
|experiential_memory_id|||
|important_level|||
|emergency_level|||

### [Problem solving result]

#### reward_categories
|Column|Type|Option|
|---|---|---|
|id|||
|reward_category_id|||
|phase|||
|name|||

#### reward_rates
|Column|Type|Option|
|---|---|---|
|id|||
|reward_category_id|||
|rate|||

### [Lifespan]

#### lifespan_categories
|Column|Type|Option|
|---|---|---|
|id|||
|max|||
|decrease_rate|||
|name|||
|name|||

#### lifespans
|Column|Type|Option|
|---|---|---|
|id|||
|lifespan_category_id|||
|remaining_amount|||
