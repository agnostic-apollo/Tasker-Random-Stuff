# Tasker Config Names Extractor

A helper script to extract tasker profile, scene or task names from a tasker config or project file.

## Usage:

```
#extract all profile names
bash tasker_config_names_extractor -p "config.xml"

#extract all scene names
bash tasker_config_names_extractor -s "config.xml"

#extract all task names
bash tasker_config_names_extractor -t "config.xml"

#extract all profile, scene and task names
tasker_file="config.xml"; echo -e "Profiles:"; bash tasker_config_names_extractor -p "$tasker_file"; echo -e "\nScenes:"; bash tasker_config_names_extractor -s "$tasker_file"; echo -e "\nTasks:"; bash tasker_config_names_extractor -t "$tasker_file";
```
