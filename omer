def turn_number_to_words (number, fem = True, reverse = False, counting = False):
    """Turns numbers (from 1 to 99) into words in hebrew."""

    # hundreds_str = [u"", u"מאה", u"מאתיים", u"שלוש מאות", u"ארבע מאות", u"חמש מאות", u"שש מאות", u"שבע מאות", u"שמונה מאות", u"תשע מאות"]
    tens_str = [u"", u"עשר", u"עשרים", u"שלושים", u"ארבעים", u"חמישים", u"שישים", u"שבעים", u"שמונים", u"תשעים"]
    ones_str = [u"", u"אחת", u"שתים", u"שלוש", u"ארבע", u"חמש", u"שש", u"שבע", u"שמונה", u"תשע", u"עשרה"]

    if not fem:
        ones_str = [u"", u"אחד", u"שנים", u"שלושה", u"ארבעה", u"חמשה", u"ששה", u"שבעה", u"שמונה", u"תשעה", u"עשרה"]
        tens_str[1] = u"עשר"

    ones = number % 10
    tens = (number % 100) // 10
    # hundreds = number//100
    order = [tens_str[tens], ones_str[ones]]
    number_str = ""
    if reverse or tens < 2:
        order.reverse()

    # if hundreds != 0:
    #     number_str += " "
    #     if tens < 2 and ones or tens !=0:
    #         number_str += u"ו"
    number_str += order[0]
    if tens == 1:
        if ones == 0:
            number_str += tens_str[tens]
        else:
            number_str += " " + ones_str[10]
    elif tens > 1:
        if ones != 0:
            number_str += " ו"
        number_str += order[1]
    if counting and number == 2:
        number_str = ones_str[ones][:-1]
    return number_str

def get_omer_string(omer):
    """Return a string representing the count of the Omer."""
    if not 0 < omer < 50:
        raise ValueError("Invalid Omer day: {}".format(omer))
    days = omer%7
    weeks = omer//7
    omer_str = u"היום "
    if omer == 1:
        omer_str += u"יום " + turn_number_to_words(omer, fem=False, reverse=True, counting=True)
    elif  1 < omer < 11:
        omer_str += turn_number_to_words(omer, fem=False, reverse=True, counting=True) + u" ימים"
    else:
        omer_str += turn_number_to_words(omer, fem=False, reverse=True, counting=True) + u" יום"
    if weeks > 0:
        omer_str += u" שהם "
        if weeks > 1:
            omer_str += turn_number_to_words(weeks, fem=False, counting=True) + u" שבועות"
        else:
            omer_str +=  u"שבוע " + turn_number_to_words(weeks, fem=False, counting=True)
        if days == 1:
            omer_str += u" ויום " + turn_number_to_words(days, fem=False, counting=True)
        elif days > 1:
            omer_str += " ו" + turn_number_to_words(days, fem=False, counting=True) + u" ימים"
    omer_str += u" לעומר"
    return omer_str

for i in range(1,50):
    print(get_omer_string(i))
