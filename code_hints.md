
Bonus Challenge: Dates
-----------------------


- Hint: Here's
  into a Python datetime nicely:

        def _fix_guardian_dates(results_list):
            for item in results_list:
                original_date = item['webPublicationDate']
                date_format = "%Y-%m-%dT%H:%M:%SZ"
                converted = datetime.strptime(original_date, date_format)
                item['python_date'] = converted


- Hint: In templating, try using the "date" filter to format a date converted
  into a Python datetime nicely:

        {{ item.python_date|date:"l F jS Y" }}


- Hint: Try using the Django Templating templatetag ifchanged in a for loop to
  give "section headers" for each date:

        {% ifchanged item.python_date|date:"l F jS Y" %}
            <div class="mb-3">
                <hr />
                <h1>{{ item.python_date|date:"l F jS Y" }}</h1>
            </div>
        {% endifchanged %}


Bonus Challenge: Pagination
----------------------------

- Hint: We can use "hidden inputs" and a form to pass along the current 

        <!-- Bonus Challenge: Pagination -->
        <div class="justify-content-center d-flex">
            {% if current_page > 1 %}
                <form>
                    <input type="hidden" name="searchterm" value="{{ search_term }}" />
                    <input type="hidden" name="stype" value="{{ search_type }}" />
                    <input type="hidden" name="page_number" value="{{ previous_page_number }}" />
                    <button class="btn btn-lg btn-primary">&laquo;</button>
                </form>
            {% endif %}

            <button class="btn btn-lg btn-secondary">{{ current_page }}</button>
        </div>

