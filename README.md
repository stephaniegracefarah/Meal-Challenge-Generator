import random

#MealChallengeGenerator

#Below is the list of all the food, maybe upgrade to sets in the future
#upgrade to exotic items in the future to add to existing lists (venison, rabbit, turtle, grasshoppers,
#capers, fish cakes, nori, alagator, bison, liver, goat, pigs feet, mahi mahi, eel, shark, frog,   etc.)
#future optimization
flavor_profiles = ['Mexican','American','mediterranean', 'French', 'asian', 'Thai', 'Indian', 'Eastern European',
                   'Caribbean', 'Cajun', 'German', 'South African', 'West African', 'East African', 'South American',
                   'Italian', 'American Barbeque', 'Tex-Mex']
proteins = ['beef', 'chicken', 'pork', 'eggs', 'tofu', 'salmon' 'brisket', 'shrimp', 'lamb', 'tuna', 'turkey',
            'tilapia', 'crawfish', 'crab', 'lobster', 'oysters', 'clams', 'bacon']
vegetables = ['potatoes', 'green peppers', 'onions', 'asparagus', 'kale', 'green beans', 'corn', 'endive', 'tomatoes',
              'broccoli', 'cauliflower', 'beets', 'sweet potatoes', 'beans', 'pumpkin', 'spaghetti squash',
              'acorn squash', 'corn', 'peas', 'cabbage', 'spinach', 'collard greens', 'zucchini', 'eggplant',
              'carrots', 'celery', 'olives', 'brussel sprout']
fruits = ['apples', 'pears', 'oranges', 'blueberries', 'strawberries', 'blackberries', 'mango', 'cantaloupe',
          'watermelon', 'pineapple', 'peaches', 'lemon',
          'lime', 'cherries', 'kiwi', 'banana', 'plantains', 'grapefruit', 'grapes', 'figs', 'avocado']
dairies = ['milk', 'yogurt', 'sour cream', 'feta', 'cheddar cheese', 'parmesan']
starches = ['rice', 'tortillas', 'pasta', 'pita bread', 'bread crumbs', 'farro', 'quinoa', 'oats', 'ramen noodles', 'grits',
            'granola']
challenge_ingredients = ['coffee', 'chocolate', 'potato chips', 'oreos', 'cola', 'fun dip', 'Neutella', 'liver']
special_ingredients = []

foods = [proteins, vegetables, fruits, dairies, starches]

#I need to be able to pick a random item from each list

#user_name = input('Name:')
user_name = 'you'


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

welcome_message = 'Hi {}, welcome to your very own Meal Challenge! \n' \
                  'You will be given a list of food to create a unique meal. \n' \
                  'Use standard pantry items in your food journey. Let your creative juices flow!'.format(user_name)

#add an option to add the challenge ingredient
def add_options():
    print('Would you like to add a challenge ingredient to test your culinary creativity?')
    quest1 = input('Yes or No?')
    if quest1 == ('Yes'):
        foods.append(challenge_ingredients)
    print('Okay!')


menu_string = '{}, and {}'.format(', '.join(menu_list[0:-1]), menu_list[-1])

print(welcome_message)
add_options()
print('Why not make a {} inspired meal with {}?'.format(style, menu_string))

#user_meal = input('What did you decide to make?')
#print('Mmm, {} that sounds tasty! Thank you for participating in the Meal Challenge!'.format(user_name))
#user_play_again = input('Do you want to play again? (Yes or No)')

#How do I add if/ statements - do these need to be functions? def play_again?
#def play_again():
#if ("yes") in user_play_again:
#print('Why not make a {} inspired meal with {}?'.format(style, menu_string))

    # if user_play_again = ('no'):
    #     print('Have a delicious day!')
    # print('That is not a valid response. Please enter Yes or No.')
    # return play_again()


#Playing around with functions and arguments:
#def play_again(answer1, answer2):
#if ('yes') in answer1
#print('this is a yes answer')
#if ('no') in answer2
#print('this is a no answer')





