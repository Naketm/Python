import string
import time
import random
import os

tn = False
tm = False

varname = []
varinfo = []
fullvarl = []

listinfo = []


i = 0

mathsymlr = '-=*/+|'
mathl = list(mathsymlr)

listcount = 0

z = 0

xy = 0

k = 0

exe = 'interpread.pr'
org = 'tempfile.txt'

digits = list('0123456789')

def TrueFalse(x,y):
  if x in varname and y in varname:
    pos1 = varname.index(x)
    pos2 = varname.index(y)

    info1 = varinfo[pos1]
    info2 = varinfo[pos2]

    global tmfunc
    
    if info1 == info2:
      tmfunc = True
    else:
      tmfunc = False
  if x == y:
    tmfunc = True
  else:
    tmfunc = False

with open(exe, 'r') as interp:
  for line in interp:
    linex = line.rstrip()

    if '#' in linex:
      continue
          
    if 'var ' in linex:
      secondsplit = linex.split(" = ")
      linesplit = secondsplit[0].split(" ")
      linesplitn = secondsplit[0].split("array ")
      
      thirdsplit = secondsplit[1].split('""')
      if '#' in linesplit[0]:
        continue

      elif 'rand' in secondsplit[1]:
        n1split = secondsplit[1].split('(')
        n2split = n1split[1].split(')')
        comsplit = n2split[0].split(',')
        if comsplit[0] in varname and comsplit[1] in varname:
          pos1 = varname.index(comsplit[0])
          pos2 = varname.index(comsplit[1])

          varinfo1 = varinfo[pos1]
          varinfo2 = varinfo[pos2]
          varname.append(linesplit[1])
          varinfo.append(random.randint(int(varinfo1),int(varinfo2)))

        else:
          varname.append(linesplit[1])
          varinfo.append(random.randint(int(comsplit[0]),int(comsplit[1])))
        
      elif 'array' in secondsplit[0]:
        nsplit = secondsplit[1].split('[')
        n2split = nsplit[1].split(']')
        comsplit = n2split[0].split(',')
        for things in comsplit:
          if not '"' in things:
            varname.append(f'{k}')
            varinfo.append(int(things))
            continue
            
          elif '"' in things:
            strings = ''.join(things)
            varname.append(f'[{k}]')
            x = list(strings)
            length = len(x) - 1
            x[0] = ''
            x[length] = ''
            thing = ''.join(x)
            varinfo.append(thing)
            k += 1
            continue
              
        varname.append(linesplit[1])
        listcount += 1 
        
      elif not '"' in secondsplit[1]:
        varname.append(linesplit[1])
        varinfo.append(int(thirdsplit[0]))
        
      else:
        newxz= list(thirdsplit[0])
        lengh = len(newxz)
        newxz[lengh - 1] = ''
        newxz[0] = ''
        fullstr = ''.join(newxz)
        varname.append(linesplit[1])
        varinfo.append(fullstr)

    if '  print' in linex:
      linesplit = linex.split('p')
      secondsplit = linesplit[1].split('(')
      thirdsplit = secondsplit[1].split(')')
      mark1 = thirdsplit[0].split('""')
      plussplit = thirdsplit[0].split('+')
      subsplit = thirdsplit[0].split('-')
      divsplit = thirdsplit[0].split('/')
      multisplit = thirdsplit[0].split('*')
      expsplit = thirdsplit[0].split('|')
      equalto = thirdsplit[0].split('=')

      if tn == True:
        if '[' in linesplit[1] and ']' in linesplit[1]:
          fn = thirdsplit[0].split('[')
          ln = fn[1].split(']')
          mn = ln[0].split(',')
          arrayname = mn[0]
          arrayspef = int(mn[1])
          if mn[0] in varname:
            print(varinfo[arrayspef])
            continue
    
        for something in mathl:
          pass
          
        markstr = list(mark1[0])
        getsymbol = markstr
        lengofsym = len(getsymbol) - 1
        lengoffinalsym = lengofsym // 2
        if '#' in linesplit[0]:
          continue
          
        elif not '"' in thirdsplit[0] and not '"' in secondsplit[1] and not markstr[lengoffinalsym] in mathl:      
          for var in mark1[0]:
            fullvarl.append(var)
            fullvar = ''.join(fullvarl)
            if len(fullvar) == len(mark1[0]):
              pos = varname.index(fullvar)
              print(varinfo[pos])
            else:
                continue
        
        elif '+' in thirdsplit[0] and not '"' in secondsplit[1]:
          if plussplit[0] in varname and plussplit[1] in varname:
            pos1 = varname.index(plussplit[0])
            pos2 = varname.index(plussplit[1])
  
            info1 = varinfo[pos1]
            info2 = varinfo[pos2]
  
            print(info1+info2)
            
          else:
            print(int(plussplit[0]) + int(plussplit[1]))
        elif '+' in thirdsplit[0] and '"' in secondsplit[1]:
          x1 = list(plussplit[0]+plussplit[1])
          lengx1 = len(x1) - 1
          x1[0] = ''
          x1[lengx1] = ''
          print(''.join(x1))
        elif '-' in thirdsplit[0] and not '"' in secondsplit[1]:
          if subsplit[0] in varname and subsplit[1] in varname:
            pos1 = varname.index(subsplit[0])
            pos2 = varname.index(subsplit[1])
  
            info1 = varinfo[pos1]
            info2 = varinfo[pos2]
  
            print(info1-info2)
            
          else:
            print(int(subsplit[0]) - int(subsplit[1]))
        elif '/' in thirdsplit[0] and not '"' in secondsplit[1]:
          if divsplit[0] in varname and divsplit[1] in varname:
            pos1 = varname.index(divsplit[0])
            pos2 = varname.index(divsplit[1])
  
            info1 = varinfo[pos1]
            info2 = varinfo[pos2]
  
            print(info1/info2)
            
          else:
            print(int(divsplit[0]) / int(divsplit[1]))
        elif '*' in thirdsplit[0] and not '"' in secondsplit[1]:
          if multisplit[0] in varname and multisplit[1] in varname:
            pos1 = varname.index(multisplit[0])
            pos2 = varname.index(multisplit[1])
  
            info1 = varinfo[pos1]
            info2 = varinfo[pos2]
  
            print(info1*info2)
            
          else:
            print(int(multisplit[0]) * int(multisplit[1]))
        elif '|' in thirdsplit[0] and not '"' in secondsplit[1]:
          if expsplit[0] in varname and expsplit[1] in varname:
            pos1 = varname.index(expsplit[0])
            pos2 = varname.index(expsplit[1])
  
            info1 = varinfo[pos1]
            info2 = varinfo[pos2]
  
            print(info1**info2)
            
          else:
            print(int(expsplit[0]) ** int(expsplit[1]))
        elif '=' in thirdsplit[0] and not '"' in secondsplit[1]:
          if equalto[0] in varname and equalto[1] in varname:
            
            pos1 = varname.index(equalto[0])
            pos2 = varname.index(equalto[1])
  
            info1 = varinfo[pos1]
            info2 = varinfo[pos2]
  
            TrueFalse(info1,info2)
            if tmfunc == True:
              print('True')
              
            elif tmfunc == False:
              print('False')
  
            else:
              print('ERROR UNKNOWN')
            
          else:
            print(int(equalto[0]) == int(equalto[1]))
        
        else:
          xyz = list(mark1[0])
          length = len(xyz) - 1
          xyz[length] = ''
          xyz[0] = ''
          res = ''.join(xyz)
          print(res)
    
    if 'print' in linex:
      linesplit = linex.split('p')
      secondsplit = linesplit[1].split('(')
      thirdsplit = secondsplit[1].split(')')
      mark1 = thirdsplit[0].split('""')
      plussplit = thirdsplit[0].split('+')
      subsplit = thirdsplit[0].split('-')
      divsplit = thirdsplit[0].split('/')
      multisplit = thirdsplit[0].split('*')
      expsplit = thirdsplit[0].split('|')
      equalto = thirdsplit[0].split('=')
      difsplit = thirdsplit[0].split('!=')

      if '[' in linesplit[1] and ']' in linesplit[1]:
        fn = thirdsplit[0].split('[')
        ln = fn[1].split(']')
        mn = ln[0].split(',')
        arrayname = mn[0]
        print(mn)
        arrayspef = int(mn[1])
        if mn[0] in varname:
          print(varinfo[arrayspef])
          continue
  
      for something in mathl:
        pass
        
      markstr = list(mark1[0])
      getsymbol = markstr
      lengofsym = len(getsymbol) - 1
      lengoffinalsym = lengofsym // 2
      if '#' in linesplit[0]:
        continue
        
      elif not '"' in thirdsplit[0] and not '"' in secondsplit[1] and not markstr[lengoffinalsym] in mathl and not '[' in thirdsplit[0]:      
        for var in mark1[0]:
          fullvarl.append(var)
          fullvar = ''.join(fullvarl)
          if len(fullvar) == len(mark1[0]):
            pos = varname.index(fullvar)
            print(varinfo[pos])
          else:
              continue
      
      elif '+' in thirdsplit[0] and not '"' in secondsplit[1]:
        if plussplit[0] in varname and plussplit[1] in varname:
          pos1 = varname.index(plussplit[0])
          pos2 = varname.index(plussplit[1])

          info1 = varinfo[pos1]
          info2 = varinfo[pos2]

          print(info1+info2)
          
        else:
          print(int(plussplit[0]) + int(plussplit[1]))
      elif '+' in thirdsplit[0] and '"' in secondsplit[1]:
        x1 = list(plussplit[0]+plussplit[1])
        lengx1 = len(x1) - 1
        x1[0] = ''
        x1[lengx1] = ''
        print(''.join(x1))
      elif '-' in thirdsplit[0] and not '"' in secondsplit[1]:
        if subsplit[0] in varname and subsplit[1] in varname:
          pos1 = varname.index(subsplit[0])
          pos2 = varname.index(subsplit[1])

          info1 = varinfo[pos1]
          info2 = varinfo[pos2]

          print(info1-info2)
          
        else:
          print(int(subsplit[0]) - int(subsplit[1]))
      elif '/' in thirdsplit[0] and not '"' in secondsplit[1]:
        if divsplit[0] in varname and divsplit[1] in varname:
          pos1 = varname.index(divsplit[0])
          pos2 = varname.index(divsplit[1])

          info1 = varinfo[pos1]
          info2 = varinfo[pos2]

          print(info1/info2)
          
        else:
          print(int(divsplit[0]) / int(divsplit[1]))
      elif '*' in thirdsplit[0] and not '"' in secondsplit[1]:
        if multisplit[0] in varname and multisplit[1] in varname:
          pos1 = varname.index(multisplit[0])
          pos2 = varname.index(multisplit[1])

          info1 = varinfo[pos1]
          info2 = varinfo[pos2]

          print(info1*info2)
          
        else:
          print(int(multisplit[0]) * int(multisplit[1]))
      elif '|' in thirdsplit[0] and not '"' in secondsplit[1]:
        if expsplit[0] in varname and expsplit[1] in varname:
          pos1 = varname.index(expsplit[0])
          pos2 = varname.index(expsplit[1])

          info1 = varinfo[pos1]
          info2 = varinfo[pos2]

          print(info1**info2)
          
        else:
          print(int(expsplit[0]) ** int(expsplit[1]))
      elif '=' in thirdsplit[0] and not '"' in secondsplit[1]:
        if equalto[0] in varname and equalto[1] in varname:
          
          pos1 = varname.index(equalto[0])
          pos2 = varname.index(equalto[1])

          info1 = varinfo[pos1]
          info2 = varinfo[pos2]

          TrueFalse(info1,info2)
          if tmfunc == True:
            print('True')
            
          elif tmfunc == False:
            print('False')

          else:
            print('ERROR UNKNOWN')
          
        else:
          print(int(equalto[0]) == int(equalto[1]))

      elif '!=' in thirdsplit[0] and not '"' in secondsplit[1]:
        if difsplit[0] in varname and difsplit[1] in varname:
          
          pos1 = varname.index(difsplit[0])
          pos2 = varname.index(difsplit[1])

          info1 = varinfo[pos1]
          info2 = varinfo[pos2]

          TrueFalse(info1,info2)
          if tmfunc == False:
            print('True')
            
          elif tmfunc == True:
            print('False')

          else:
            print('ERROR UNKNOWN')
          
        else:
          print(int(difsplit[0]) != int(difsplit[1]))
      
      else:
        xyz = list(mark1[0])
        length = len(xyz) - 1
        xyz[length] = ''
        xyz[0] = ''
        res = ''.join(xyz)
        print(res)
    
    if 'input >' in linex:
      namesplit = linex.split(' = ')
      secsplit = linex.split('> ')
      strsplit = secsplit[1].split('""')
      if '#' in secsplit[0]:
        continue
      if not '"' in secsplit[1] and not 'int!' in linex:
        print(f'\033[31mERROR: Broken string at [line {linex}]')
        break
      if 'int!' in secsplit[0]:
        listsec = secsplit[1]

        inp = input(listsec)
        
        varname.append(namesplit[0])
        varinfo.append(int(inp))
      else:
        fullstrsplit = list(strsplit[0])
        fullstrsplit[0] = ''
        leng = len(fullstrsplit) - 1
        fullstrsplit[leng] = ''
        fullstrsplit = ''.join(fullstrsplit)
        inp = input(fullstrsplit)

        varname.append(namesplit[0])
        varinfo.append(inp)

    if 'sleep' in linex:
      linez = linex.split('[')
      ln = linez[1].split(']')
      if '"' in linex:
        print('\033[31mERROR: String in integer format.')
        break
      elif ln[0] in varname:
        pos = varname.index(ln[0])
        time.sleep(varinfo[pos])
      else:
        time.sleep(float(ln[0]))

    else:
      continue
