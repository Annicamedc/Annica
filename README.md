## Summary
# EcoMeal AI

Final project for the Building AI course

## Summary
EcoMeal AI recommends personalized, eco-friendly meal plans based on dietary preferences, nutritional needs, and carbon footprint. Users get healthy meals that are sustainable, helping them make environmentally conscious food choices.  
*Building AI course project*

## Background
Many people want to eat healthily while reducing environmental impact, but finding sustainable meals is time-consuming.  
* Common problem: balancing nutrition, taste, cost, and sustainability.  
* Motivation: Make it easier for individuals to contribute to climate action through daily food choices.  
* Importance: Food production contributes significantly to greenhouse gas emissions; small individual changes add up.

## How is it used?
* Users input dietary preferences, restrictions (vegan, gluten-free, allergies), and calorie goals.  
* AI suggests meal plans meeting nutritional needs while minimizing environmental impact.  
* Users can swap ingredients while keeping meals eco-friendly.  
* Environment: mobile app or web platform. Users: students, families, health-conscious individuals.  

![EcoMeal AI Example](https://upload.wikimedia.org/wikipedia/commons/thumb/4/42/Food_and_environment.jpg/640px-Food_and_environment.jpg)

*Example code snippet:*  
```python
import pandas as pd
from sklearn.neighbors import NearestNeighbors

data = pd.DataFrame({
    'meal': ['Veggie Bowl', 'Chicken Salad', 'Tofu Stir Fry'],
    'calories': [500, 650, 550],
    'protein': [20, 40, 25],
    'carbon_kg': [1.2, 3.5, 0.8]
})

X = data[['calories', 'protein', 'carbon_kg']]
model = NearestNeighbors(n_neighbors=1)
model.fit(X)

target = [[550, 25, 1.0]]
distance, index = model.kneighbors(target)
print("Recommended meal:", data.iloc[index[0][0]]['meal'])
