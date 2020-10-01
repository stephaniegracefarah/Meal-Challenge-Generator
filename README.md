import random

#MealChallengeGenerator

#Below is the list of all the food
flavor_profiles = ['Mexican','American','mediterranean', 'French', 'asian', 'Thai', 'Indian', 'Eastern European',
                   'Caribbean', 'Cajun', 'German', 'South African', 'West African', 'East African', 'South American',
                   'Italian', 'American barbeque', 'Tex-Mex']
proteins = ['beef', 'chicken', 'pork', 'eggs', 'tofu', 'salmon', 'brisket', 'shrimp', 'lamb', 'tuna', 'turkey',
            'tilapia', 'crawfish', 'crab', 'lobster', 'oysters', 'clams', 'bacon']
vegetables = ['potatoes', 'green peppers', 'onions', 'asparagus', 'kale', 'green beans', 'corn', 'endive', 'tomatoes',
              'broccoli', 'cauliflower', 'beets', 'sweet potatoes', 'beans', 'pumpkin', 'spaghetti squash',
              'acorn squash', 'corn', 'peas', 'cabbage', 'spinach', 'collard greens', 'zucchini', 'eggplant',
              'carrots', 'celery', 'olives', 'brussel sprout']
fruits = ['apples', 'pears', 'oranges', 'blueberries', 'strawberries', 'blackberries', 'mango', 'cantaloupe',
          'watermelon', 'pineapple', 'peaches', 'lemon',
          'lime', 'cherries', 'kiwi', 'banana', 'plantains', 'grapefruit', 'grapes', 'figs', 'avocado']
dairies = ['milk', 'yogurt', 'sour cream', 'feta', 'cheddar cheese', 'parmesan']
starches = ['rice', 'tortillas', 'pasta', 'pita bread', 'bread crumbs', 'farro', 'quinoa', 'oats', 'ramen noodles',
            'grits',
            'granola']
challenge_ingredients = ['marshmallows','coffee', 'chocolate', 'potato chips', 'oreos', 'cola', 'fun dip', 'Neutella',
                         'liver', 'nori']

foods = [proteins, vegetables, fruits, dairies, starches]

print('\nTo start your meal challenge, please enter your name.')
#user_name = input('Name:')
user_name = 'you'
style = random.choice(flavor_profiles)
welcome_message = '\nHi {}, welcome to your very own Meal Challenge! \n' \
                  'You will be given a list of food to create a unique meal. \n' \
                  'Use standard pantry items in your food journey, and let your creative juices flow!\n'.format(user_name)
print(welcome_message)

#challenge ingredient option
def add_options():
    print('Would you like to add a challenge ingredient to test your culinary creativity?')
    #'Right now, the categories of foods that you will use are:' list of foods - how do I do that without listing the list of lists?
    quest1 = input('Yes or No?')
    if len(foods) > 5:
        foods.pop(-1)
    if quest1.lower().lstrip() == ('yes'):
        foods.append(challenge_ingredients)
    elif quest1.lower().lstrip() == ('no'):
        print('\nSounds good, no extra ingredient will be added.')
    else:
        print('\nPlease enter a valid response.')
        add_options()

#what we are cooking with
def menu_list_function():
    menu_list = []
    for food in foods:
        selected_food = random.choice(food)
        menu_list.append(selected_food)
    return menu_list

def menu_suggestion():
    menu_list = menu_list_function()
    menu_string = '{}, and {}'.format(', '.join(menu_list[0:-1]), menu_list[-1])
    # if first word in printed flavor profile is a vowel, change a to an - how do I do that? menu_string.replace('and', 'an')
    print('\nOkay! Why not make a:\n\n*** {} inspired meal with: {}?***\n'.format(style, menu_string))
    #star frame around printed menu, bottom and top lines need to equal the len of the string - how do I do that?
    #What did you decide to make? And store it in a list, and at the end of the game, print the list. 

def repeat():
    print('Would you like to try a new combination?')
    quest2 = (input('Yes or No?'))
    if quest2.lower().lstrip() == ('yes'):
        menu_list_function()
        menu_suggestion()
        repeat()
    elif quest2.lower().lstrip() == ('no'):
        print('\nOkay! Thank you for participating in the meal challenge!')
    else:
        print('\nPlease enter a valid response.\n')
        repeat()

add_options()
menu_suggestion()
repeat()


