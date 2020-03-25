# Sphinx

[Дока](https://www.sphinx-doc.org/en/master/)

	
	
## Сделаем ВО.

	python -m venv venv
	
## Установка

	pip install -U sphinx sphinx-autobuild sphinxcontrib-plantuml==0.17.1
	
	
	

	
## Старт.

	sphinx-quickstart

## Сборка.

	sphinx-build -b html source build
	
## Запуск.

	cd myproject
	python -m http.server 8080

## Темы.

[Каталог](https://sphinx-themes.org/)

### conf.py

	html_theme = 'nature'

	nature classic

## Расширения


	extensions = [
		'sphinx.ext.autodoc',
		'sphinxcontrib.plantuml'
	]
	plantuml = 'java -jar /home/zdimon/plantuml/plantuml.jar'

	import os
	import sys
	import django
	sys.path.insert(0, os.path.abspath('../backend'))
	os.environ['DJANGO_SETTINGS_MODULE'] = 'backend.settings'
	django.setup()

	import inspect
	from django.utils.html import strip_tags

	def process_docstring(app, what, name, obj, options, lines):
		# This causes import errors if left outside the function
		from django.db import models

		# Only look at objects that inherit from Django's base model class
		if inspect.isclass(obj) and issubclass(obj, models.Model):
			# Grab the field list from the meta class
			fields = obj._meta.fields

			for field in fields:
				# Decode and strip any html out of the field's help text
				help_text = strip_tags(field.help_text)

				# Decode and capitalize the verbose name, for use if there isn't
				# any help text
				verbose_name = field.verbose_name

				if help_text:
					# Add the model field to the end of the docstring as a param
					# using the help text as the description
					lines.append(u':param %s: %s' % (field.attname, help_text))
				else:
					# Add the model field to the end of the docstring as a param
					# using the verbose name as the description
					lines.append(u':param %s: %s' % (field.attname, verbose_name))

				# Add the field's type to the docstring
				lines.append(u':type %s: %s' % (field.attname, type(field).__name__))

		# Return the extended docstring
		return lines


	def setup(app):
		# Register the docstring processor with sphinx
		app.connect('autodoc-process-docstring', process_docstring)


### PlantUML

	https://www.java.com/ru/download/manual.jsp
	
	https://plantuml.com/ru/download
	
## RST format

[Дока](https://docutils.sourceforge.io/docs/user/rst/quickref.html)

Index.rst

	.. toctree::
		:maxdepth: 2
		:caption: Utils:

		modules/utils/load_data.rst
	

Code 

	.. code::

		  case Actions.ActionTypes.LogOut:

			return {
			  ...state,
			  token: '',
			  is_auth: false,
			  user: {}
			};

Image

	.. image:: ../images/design/chat.png
	
Link 

	
Diagrams

	.. uml::

		@startuml

		[Base Component]

		
		[My photo Component]
		[Favorites Component]
		[Subscribers Component]
		

		[Info Component]
		[Gallery Component]
		[Feed Component] --> [Feed Item]
		

		@enduml

