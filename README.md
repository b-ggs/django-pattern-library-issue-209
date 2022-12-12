# Demo project for django-pattern-library issue [#209](https://github.com/torchbox/django-pattern-library/issues/209)

## Relevant templates

- [`page_body.html`](https://github.com/b-ggs/django-pattern-library-issue-209/blob/main/project_styleguide/templates/patterns/components/page_body.html) - A template that represents a page's body. In this demo it just `include`s a call-to-action component.
- [`call_to_action.html`](https://github.com/b-ggs/django-pattern-library-issue-209/blob/main/project_styleguide/templates/patterns/components/call_to_action.html) - A call-to-action component template that uses an `include_block` from Wagtail to display a button.
- [`button.html`](https://github.com/b-ggs/django-pattern-library-issue-209/blob/main/project_styleguide/templates/patterns/components/button.html) - A button component template used by the call-to-action component.


## Steps to reproduce:

1. Install `django-pattern-library==1.0.0`, Django 3.2 LTS, and Wagtail 4.1.1 with the included `requirements.txt`

```bash
pip install -r requirements-pattern-library-1.0.0.txt
```

2. Run the development server

```bash
./manage.py runserver 0:8000
```

3. Navigate to the pattern library at http://localhost:8000/pattern-library/

4. Visit the `button.html` and `call_to_action.html` components, observe that the templates load properly

5. Visit the `page_body.html` component.


### Expected result

The template is displayed, as in `django-pattern-library==0.6.0`. (Click to enlarge)

<img src="https://user-images.githubusercontent.com/6130147/207022164-64c5168b-1d41-4a96-88de-7a2c39176efb.png" width="500" />


### Actual result

A `TypeError` is raised on `django-pattern-library==0.7.0` and later.  (Click to enlarge)

<details>
  <summary>Stack trace</summary>

```python
[12/Dec/2022 10:17:37] "GET /pattern-library/pattern/patterns/components/page_body.html HTTP/1.1" 200 5764
Internal Server Error: /pattern-library/render-pattern/patterns/components/page_body.html
Traceback (most recent call last):
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/core/handlers/exception.py", line 47, in inner
    response = get_response(request)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/core/handlers/base.py", line 181, in _get_response
    response = wrapped_callback(request, *callback_args, **callback_kwargs)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/views/generic/base.py", line 70, in view
    return self.dispatch(request, *args, **kwargs)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/views/generic/base.py", line 98, in dispatch
    return handler(request, *args, **kwargs)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/utils/decorators.py", line 43, in _wrapper
    return bound_method(*args, **kwargs)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/views/decorators/clickjacking.py", line 33, in wrapped_view
    resp = view_func(*args, **kwargs)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/pattern_library/views.py", line 95, in get
    rendered_pattern = render_pattern(request, pattern_template_name)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/pattern_library/utils.py", line 227, in render_pattern
    return render_to_string(template_name, request=request, context=context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/loader.py", line 62, in render_to_string
    return template.render(context, request)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/backends/django.py", line 61, in render
    return self.template.render(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/base.py", line 170, in render
    return self._render(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/base.py", line 162, in _render
    return self.nodelist.render(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/base.py", line 938, in render
    bit = node.render_annotated(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/base.py", line 905, in render_annotated
    return self.render(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/pattern_library/loader_tags.py", line 82, in render
    output = super().render(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/loader_tags.py", line 195, in render
    return template.render(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/base.py", line 172, in render
    return self._render(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/base.py", line 162, in _render
    return self.nodelist.render(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/base.py", line 938, in render
    bit = node.render_annotated(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/base.py", line 905, in render_annotated
    return self.render(context)
  File "/Users/joshua/dev/b-ggs/django-pattern-library-issue-209/venv/lib/python3.9/site-packages/django/template/defaulttags.py", line 221, in render
    return mark_safe(''.join(nodelist))
TypeError: sequence item 1: expected str instance, NoneType found
```

</details>

<img src="https://user-images.githubusercontent.com/6130147/207022353-905d4b19-cd77-424e-885b-efd9d26bf372.png" width="500" />
