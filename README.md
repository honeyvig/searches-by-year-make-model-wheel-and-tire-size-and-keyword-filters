# searches-by-year-make-model-wheel-and-tire-size-and-keyword-filters
Below is a Python code outline for performing searches by year, make, model, wheel and tire size, and keyword filters. This structure assumes you have a data source (like a list or database) of vehicles and related information. You can customize it according to the specifics of your dataset or database structure.
Sample Python Code

# Sample Data (replace with your actual data structure)
vehicles_data = [
    {'year': 2020, 'make': 'Toyota', 'model': 'Camry', 'wheel_size': '18', 'tire_size': '225/50R18', 'keywords': ['sedan', '4-door', 'gas']},
    {'year': 2021, 'make': 'Honda', 'model': 'Civic', 'wheel_size': '17', 'tire_size': '205/55R17', 'keywords': ['compact', '4-door', 'gas']},
    {'year': 2019, 'make': 'Ford', 'model': 'F-150', 'wheel_size': '20', 'tire_size': '275/65R20', 'keywords': ['pickup', 'truck', '4-door']},
    # Add more vehicle records...
]

# Search by year, make, and model
def search_by_year_make_model(year=None, make=None, model=None):
    results = []
    for vehicle in vehicles_data:
        if (year is None or vehicle['year'] == year) and \
           (make is None or vehicle['make'].lower() == make.lower()) and \
           (model is None or vehicle['model'].lower() == model.lower()):
            results.append(vehicle)
    return results

# Search by wheel and tire size
def search_by_wheel_tire_size(wheel_size=None, tire_size=None):
    results = []
    for vehicle in vehicles_data:
        if (wheel_size is None or vehicle['wheel_size'] == wheel_size) and \
           (tire_size is None or vehicle['tire_size'] == tire_size):
            results.append(vehicle)
    return results

# Search by keywords and filters
def search_by_keywords_and_filters(keywords=None, filters=None):
    results = []
    for vehicle in vehicles_data:
        matches_keywords = all(keyword.lower() in [k.lower() for k in vehicle['keywords']] for keyword in (keywords or []))
        matches_filters = all(vehicle.get(k) == v for k, v in (filters or {}).items())
        if matches_keywords and matches_filters:
            results.append(vehicle)
    return results

# Example Searches:

# Search by year, make, and model
year_make_model_results = search_by_year_make_model(year=2020, make='Toyota', model='Camry')
print("Search by year, make, model results:", year_make_model_results)

# Search by wheel and tire size
wheel_tire_results = search_by_wheel_tire_size(wheel_size='18', tire_size='225/50R18')
print("Search by wheel and tire size results:", wheel_tire_results)

# Search by keywords and filters
keywords_filters_results = search_by_keywords_and_filters(keywords=['4-door'], filters={'year': 2021})
print("Search by keywords and filters results:", keywords_filters_results)

Explanation:

    search_by_year_make_model: This function searches for vehicles by their year, make, and model. You can pass None for any parameter if you don't want to filter by that field.

    search_by_wheel_tire_size: This function searches for vehicles based on wheel size and tire size. Again, you can pass None if you want to omit a specific filter.

    search_by_keywords_and_filters: This function performs a search based on a list of keywords (like ['sedan', 'gas']) and optional additional filters (such as filtering by the vehicle's year). It combines both keyword matching and exact matching for other attributes (e.g., year, make).

Customization:

    You can expand the search criteria (like adding additional vehicle attributes) as per your requirements.
    The data can be retrieved from a database, an API, or any other source, so you might want to modify the vehicles_data source.
