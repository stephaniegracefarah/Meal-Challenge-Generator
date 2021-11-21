mport random
import textwrap

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

creations = []

foods = [proteins, vegetables, fruits, dairies, starches]

print('\nTo start your meal challenge, please enter your name.')
user_name = input('Name:')
# user_name = 'you'

welcome_message = '\nHi {}, welcome to your very own Meal Challenge! \n' \
                  'You will be given a list of food to create a unique meal. \n' \
                  'Use standard pantry items in your food journey, and let your creative juices flow!\n'.format(user_name)
print(welcome_message)

#makes lists look better
def format_list(raw_list):
    if not len(raw_list):
        return 'nothing'
    if len(raw_list) == 1:
        return raw_list[0]
    if len(raw_list) == 2:
        return ' and '.join(raw_list)
    return '{}, and {}'.format(', '.join(raw_list[0:-1]), raw_list[-1])


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

#printing what we are cooking with
def menu_suggestion():
    menu_list = menu_list_function()
    menu_string = textwrap.fill(format_list(menu_list))
    style = random.choice(flavor_profiles).capitalize()
    suggested_creation = '*** {} inspired meal with {}? ***'.format(style, menu_string)
    star_string_long = '*' * len(suggested_creation)
    star_string_short = '*' * 3 + ' ' * (len(suggested_creation) - 6) + '*' * 3
    print('\nOkay! Why not make {}: \n\n{}\n{}\n{}\n{}\n{}\n{}\n{}\n'.format(
        'an' if style[0].lower() in ['a', 'e', 'i', 'o', 'u'] else 'a',
        star_string_long,
        star_string_short,
        star_string_short,
        suggested_creation,
        star_string_short,
        star_string_short,
        star_string_long,
    ))
    creation = input('What did you decide to make?')
    if len(creation.lstrip()):
        creations.append(creation.lstrip())

#better way to repeat
def repeat_iter():
    quest2 = ''
    while quest2.lower().lstrip() != 'no':
        print('Would you like to try a new combination?')
        quest2 = (input('Yes or No?'))
        if quest2.lower().lstrip() == ('yes'):
            menu_list_function()
            menu_suggestion()
        elif quest2.lower().lstrip() == ('no'):
            print('\nOkay! Thank you for participating in the meal challenge!')
        else:
            print('\nPlease enter a valid response.\n')

def display_creations():
    print(textwrap.fill('Great job! Today, you made {}. Happy cooking!'.format(format_list(creations))))

add_options()
menu_suggestion()
repeat_iter()
display_creations()
