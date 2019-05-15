# Make Popup dialog by using bootstrap on dJango. 

1. pip install django-bootstrap-modal-forms. It's basic step. 
2. Add 'bootstrap_modal_forms' in INSTALLED_APPS on settings.py. 
3. download bootstrap.js, jquery.bootstrap.modal.forms.js, bootstrap.css. 
4. make forms.py source -> add your form. 
5. add CRUD method in views.py. it is necessary that import from bootstrap_modal_forms.generic import BSModalCreateView, BSModalUpdateView, BSModalDeleteView. 
6. create popup html.
7. add a button function {% formurl: `formurl` %}.
8. add to url.py `formurl`
