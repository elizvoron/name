Добавление в таблицу с внешним ключом


con = sqlite3.connect("names.sqlite")
cur = con.cursor()
cur.execute(f"INSERT INTO tests(test, fi) SELECT '{ts}', id FROM name WHERE fio = '{fi}'")
con.commit()
con.close()# name


ввод в таблицу без внешнего ключа

con = sqlite3.connect("names.sqlite")
cur = con.cursor()
cur.execute(f'INSERT INTO name(fio) VALUES("{self.fii}")')
con.commit()
con.close()

изменение значения


con = sqlite3.connect("names.sqlite")
cur = con.cursor()
cur.execute(f"UPDATE tests SET ress = {self.n} WHERE test = '{ts}' AND fi = (SELECT id FROM name WHERE fio = '{fi}')")
con.commit()
con.close()



вывод в список 

con = sqlite3.connect("names.sqlite")
cur = con.cursor()
result = cur.execute(f"SELECT test, ress FROM tests WHERE fi = (SELECT id FROM name WHERE fio = '{fi}')").fetchall()
