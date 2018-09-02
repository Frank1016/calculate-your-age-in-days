# calculate-your-age-in-days
# Given your birthday and the current date, calculate your age in days.  Account for leap days. Assume that the birthday and current date are correct dates (and no time travel).

def test_year(a):
    if a / 4 * 4 == a:
        return 366
    return 365
    
def test_month(a,y):
    if a == 1 or a == 3 or a == 5 or a == 7 or a == 8 or a == 10 or a == 12:
        return 31
    if a == 2:
        if test_year(y) == 366:
            return 29
        return 28
    return 30
    

def daysBetweenDates(year1, month1, day1, year2, month2, day2):
    if year1 == year2:
        if month1 == month2:
            return day2 - day1
        i = month1 + 1
        days = test_month(month1,year1) - day1
        while i < month2:
            days = days + test_month(i,year1)
            i = i + 1
        return days + day2
    else:
        days = test_month(month1,year1) - day1
        i1 = month1 + 1
        while i1 <= 12:
            days = days + test_month(i1,year1)
            i1 = i1 + 1
        j = year1 + 1
        while j < year2:
            days = days + test_year(j)
            j = j + 1
        i2 = 1
        while i2 < month2:
            days = days + test_month(i2,year2)
            i2 = i2 + 1
        return days + day2
    
