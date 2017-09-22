# usda_db_tool
Tool built around USDA's API to look up foods and nutrients with commands to save to an sqlite db.

To look up the USDA's food ID using a search term:

    ndbno_term = client.search('cheese')  # returns a (food ID, food name) tuple

You can then save that food ID, food name record to the sqlite database:

    client.add_food(ndbno_term)

To pull a list of a food's nutrients and the associated values once you have the food's ID:

    nutrient_ids_values = client.food_report(ndbno)  # if you already have the food's ID separately
    nutrient_ids_values = client.food_report(ndbno_term[0])  # if you want to use the food ID from the client.search() result
    
To add the food's nutrient information to the sqlite database:

    client.add_food_nutrients(nutrient_ids_values)
