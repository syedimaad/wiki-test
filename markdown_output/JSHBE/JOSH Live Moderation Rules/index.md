following are the classes and respective thresholds considered from the
hive response to determine and moderate whether the image
is **SFW/NSFW**:

\"general_nsfw\": 0.1, \"general_suggestive\": 0.5,
\"yes_child_present\": 0.9, \"yes_sexual_activity\": 0.5,
\"yes_female_underwear\": 0.5, \"yes_male_underwear\": 0.5,
\"yes_sex_toy\": 0.5, \"yes_female_nudity\": 0.5, \"yes_male_nudity\":
0.5, \"yes_female_swimwear\": 0.5, \"yes_male_shirtless\": 0.5,
\"gun_in_hand\": 0.5, \"knife_in_hand\": 0.5, \"very_bloody\": 0.5,
\"hanging\": 0.5, \"yes_pills\": 0.5, \"illicit_injectables\": 0.5,
\"yes_smoking\": 0.5, \"yes_nazi\": 0.5, \"yes_terrorist\": 0.5,
\"yes_kkk\": 0.5, \"yes_middle_finger\": 0.5, \"noose\": 0.5,
\"yes_emaciated_body\": 0.5, \"human_corpse\": 0.5, \"animated_corpse\":
0.5, \"yes_self_harm\": 0.5, \"yes_realistic_nudity\": 0.5
\"yes_gambling\": 0.5 \"yes_undressed\": 0.5 \"yes_confederate\": 0.5
\"animated_alcohol\": 0.5 \"yes_alcohol\": 0.5 \"yes_pfi\":0.9

we are defining rules as follows for moderating the JOSH Live Rooms:\
from the above-defined classes, we are not considering the following:\
`general_suggestive, yes_child_present, knife_in_hand, yes_middle_finger, human_corpse`

### Confidence Score 10 for shutting down the Room:

A Confidence score of 10 will be given for the frame if the hive
responds with higher thresholds for any of the below classes.

\"general_nsfw\": 0.9 \"yes_sexual_activity\": 0.8 \"yes_sex_toy\": 0.8
\"yes_female_nudity\": 0.6 \"yes_male_nudity\": 0.7 \"gun_in_hand\": 0.8
\"very_bloody\": 0.8 \"hanging\": 0.8 \"yes_smoking\": 0.8
\"yes_self_harm\": 0.9 \"yes_middle_finger\": 0.9

### Confidence Score 7 for Warning:

A Confidence score of 7 will be given for the frame if the hive responds
with higher thresholds for any of the below classes and the threshold is
lower than that of a Confidence Score of 10.

\"general_nsfw\": 0.8 \"yes_sexual_activity\": 0.7 \"yes_sex_toy\": 0.8
\"yes_female_nudity\": 0.5 \"yes_male_nudity\": 0.5 \"yes_smoking\": 0.7
\"yes_self_harm\": 0.8 \"yes_middle_finger\": 0.8 \"gun_in_hand\": 0.7
\"very_bloody\": 0.7 \"hanging\": 0.7 \"yes_smoking\": 0.7
\"yes_self_harm\": 0.8

the evaluation will be done from a confidence score of 10 to lower and
if any conditions are not met then a Confidence score of 5 will be
given.
