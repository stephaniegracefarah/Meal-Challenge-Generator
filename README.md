import random

#MealChallengeGenerator

#Below is the list of all the food, maybe upgrade to sets in the future
flavor_profiles = ['Mexican','American','mediterranean', 'French', 'asian', 'Thai']
proteins = ['beef', 'chicken', 'pork', 'eggs', 'tofu', 'salmon']
vegetables = ['potatoes', 'green peppers', 'onions', 'asparagus', 'kale']
fruits = ['apples', 'pears', 'oranges', 'berries', 'mango']
dairies = ['milk', 'yogurt', 'sour cream', 'feta', 'cheddar cheese']
starches = ['rice', 'tortillas', 'noodles']
special_ingredients = []


foods = [proteins, vegetables, fruits, dairies, starches]

#I need to be able to pick a random item from each list

#user_name = input('Name:')
user_name = 'Pebbles'


#special ingredient user addition option
#added_ingredient = input('Hi {}! Please add a special ingredient to the menu: '.format(user_name))
#special_ingredients.append(added_ingredient)
#foods.append(special_ingredients)

#standard (no special ingredient option)
menu_list = []
for food in foods:
    selected_food = random.choice(food)
    menu_list.append(selected_food)

style = random.choice(flavor_profiles)

menu_string = '{}, and {}'.format(', '.join(menu_list[0:-1]), menu_list[-1])
print('Hi {}! Why not make a {} inspired meal with {}?'.format(user_name, style, menu_string))
