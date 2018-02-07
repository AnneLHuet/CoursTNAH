Python chapitre 11 - Thibault Clérice

# Chapitre 11 - Jointures SQL et Update

## La jointure

* Attention : peut rapidement poser des problèmes de performance sur le temps d'exécution de la requête

* les relations n-n 
	* une table de liaison permet de conserver ces liens

* http://docs.sqlalchemy.org/en/latest/orm/basic_relationships.html
	* donne des exemples de tous les types de jointures

* `db.ForeignKey('nomtable.nomchamp') `

* `default=datetime.datetime.utcnow`

* `__tablename__`

* `db.relationship("Authorship", back_populates="user")`