# Менять заголовок функции нельзя
def get_rooms_for_class(class_id: str) -> str:
    with open('timetable_dict.json', 'r') as f_read:
        timetable = json.load(f_read)
    resultat = []
    for i in range(len(timetable[class_id])):
      number = str(i+1)
      rooms = str(timetable[class_id][number]["room"])
      resun = number + "." + " " + rooms + "\n"
      resultat.append(resun)
    reson = ''.join(resultat)
    result = '<{}>'.format(reson)
    return result
# Пример и проверка. Это удалять нельзя.
TIMETABLE_FOR_5S = '''1. 201
2. street
3. 209
4. 209
5. актовый зал
6. актовый зал
7. 401
8. 401
'''
print(get_rooms_for_class('5s'))
assert(get_rooms_for_class('5s') == "<{}>".format(TIMETABLE_FOR_5S))
