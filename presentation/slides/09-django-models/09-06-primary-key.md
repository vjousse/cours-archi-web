## Clé primaire

Par défaut, Django ajoute un champ

```python
id = models.AutoField(primary_key=True)
```

Si vous spécifiez votre clé primaire, ce champ n'est pas ajouté.
