# Meal-Challenge-Generator
A generator that gives a user a random collection of food items to create a unique meal. 


import random

#MealChallengeGenerator

#Below is the list of all the food, maybe upgrade to sets in the future
proteins = ['beef', 'chicken', 'pork', 'eggs', 'tofu', 'salmon']
vegetables = ['potatoes', 'green peppers', 'onions', 'asparagus', 'kale']
fruits = ['apples', 'pears', 'oranges', 'berries', 'mango']
dairies = ['milk', 'yogurt', 'sour cream', 'feta', 'cheddar cheese']
starches = ['rice', 'tortillas', 'noodles']
special_ingredients = []
flavor_profiles = ['Mexican','American','Mediterranean', 'French', 'Asian', 'Thai']

foods = [proteins, vegetables, fruits, dairies, starches]

#I need to be able to pick a random item from each list

user_name = input('Name:')
# user_name = 'Pebbles'
added_ingredient = input('Hi {}! Please add a special ingredient to the menu: '.format(user_name))
special_ingredients.append(added_ingredient)
foods.append(special_ingredients)

menu_list = []
for food in foods:
    selected_food = random.choice(food)
    menu_list.append(selected_food)

menu_string = '{}, and {}'.format(', '.join(menu_list[0:-1]), menu_list[-1])
print('Why not make a meal with {}?'.format(menu_string))
