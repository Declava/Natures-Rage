# Nature's Rage
**Nature's Rage** (NR) is an adaptation of the Nature's Rage RP as a total conversion mod for Victoria 3.
## Installation Guide
To download the NR mod, simply click the green "Code" button then click "Download ZIP". Once downloaded, extract the .zip file into **C:\Users\yourusernamehere\Documents\Paradox Interactive\Victoria 3\mod** and then add the mod to the playset you have enabled in the launcher.
### Install for use with VSCode and Git
If you want to use VSCode to contribute to the project instead of directly using the GitHub page, [install Git](https://git-scm.com/install/windows) and run "git clone https://github.com/Declava/Natures-Rage.git" in Command Prompt then open the resulting NR mod folder in VSCode, doing so should automatically enable the Source Control feature to allow you to easily push your changes to the GitHub repository right from VSCode itself.
## Contributor Guide
If you're unfamiliar with Victoria 3 modding, below are a few easy ways to contribute to the project and make my life easier. To be able to edit anything to begin with, please ask me to be added as a GitHub collaborator.
### Adding Flags
To add any flags that are missing for certain countries in the mod, you must name them "countrynamehere_coa.png", or "countrynamehere_ideology_coa.png" for dynamic flags, then upload them into the **gfx/coat_of_arms/textured_emblems** folder. 

Usually there are a few more steps to actually implement the flag ingame, but I'll handle those.
### Adding Country Laws
To add or correct any laws for countries in the mod, head on over to **common/history/countries** and find the country file with the laws you want to change. For example, you can type "activate_law = law_type:law_private_health_insurance" to add private healthcare as a law for your country.
### Adding Pops
Accurate representations of national populations from the Nature's Rage RP are currently beyond the scope of the mod, but you are free to make them yourself by heading into **common/history/pops** and selecting (or creating if missing) the region file where you are adding the pops. Below is a simple format for adding your pops:

Example Format:
```
	s:STATE_SAVOY = { # Incase you don't know what state your given location is part of, just ask me or let me correct the code once I'm notified of the change.
		region_state:TAR = { # Replace the tag for Tarsina "TAR" with the tag for the country you want to add the pops to.
			create_pop = {
				religion = darmonist
				culture = tarsinian
				size = 6767676767
			}
		}
	}
```
### Adding City Names
To rename city names with your own ones from the RP or new original names, head over to **localization/english/hub_names_l_english.yml** and then find the city you want to rename using Ctrl+F.
### Adding State Names
To rename state names, head over to **localization/english/map/nr_states_l_english.yml** and then find the state you want to rename using Ctrl+F.
### Adding Flavour Text
To add flavour text for your country (the lore text you see for countries in the country selection screen) head over to **localization/english/country_flavor_text_l_english.yml** and find your country's tag then start writing. If you don't know what three-letter tag it has, ask me.
### Adding Ideologies
To add original ideologies, head over to **common/ideologies/nr_leader_ideologies.txt** and follow the format.

Example Format:
```
ideology_example = {
	icon = "gfx/interface/icons/ideology_icons/ideology_leader/ideology_leader_royalist.dds"
	
	character_ideology = yes
	
	lawgroup_governance_principles = {
		law_monarchy = strongly_approve
		law_presidential_republic = neutral
		law_parliamentary_republic = disapprove
		law_council_republic = strongly_disapprove
	}
}
```

To localize your ideologies with names and descriptions, head over to **localization/english/laws_l_english.yml**.
### Adding Characters
To add new characters, first you need to **common/history/characters** and select the country you want to make a character for or create it yourself if the country you are selecting doesn't have any characters yet. Next you need to use this format below:
```
		create_character = {
		# John Character of Country
			first_name = "john_character_first_name" # First and last name is defined in localization/english/nr_characters_l_english.yml
			last_name = "john_character_last_name"
			ruler = yes
			ig_leader = no # "ig" means Interest Group
			noble = yes
			historical = yes
			age = 18
			dna = dna_john_character # "dna" is for an optional custom character appearance which can be created in common/dna_data. It is recommended to use the portrait editor ingame to generate this dna data by running "portrait_editor" in the console with debug mode enabled.
			culture = cu:tarsinian # For a list of possible cultures, head to common/cultures/zz_nr_cultures.txt in the mod files.
			female = no
			religion = rel:darmonist
			interest_group = ig_industrialists
			ideology = ideology_market_liberal # For a list of possible ideologies, head to common/ideologies in the vanilla game files.
			traits = {
				ambitious # For a list of possible traits, head to common/character_traits in the vanilla game files.
			}
			commander_usage = { # Do not add this section if not a commander.
				country_trigger = {
					c:TAR ?= THIS # Replace the tag for Tarsina "TAR" with the tag for your country
				}
				role = general
				earliest_usage_date = 1852.1.1
				latest_usage_date = 6767.1.1
			}
			commander_rank = default
			home_region = STATE_BRANDENBURG
		}
```
### Adding anything else
For adding anything else, you can suggest to me what you want added, send me graphical assets I can use for stuff, or try to implement it yourself by familiarising yourself with the structure of the mod and looking for the area of the game to modify.