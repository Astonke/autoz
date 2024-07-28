#autoz usage
pip install autoz

#NB -> the functions only take in xpath

#script
from autoz.kit import *
from time import sleep

#init drivers, browser bin, background features
#the script will run in background unless background is set to False
init()

#go to a page
go('https://odibets.com/live/')


# Search button
find_click('/html/body/div[1]/div/div[2]/div[1]/div[3]')

# Input area
find_click('//*[@id="modal"]/div/div[1]/input')

# Enter code
clear_input('//*[@id="modal"]/div/div[1]/input', '1127')

# Teams
home = extract_text('/html/body/div[1]/div/div[8]/div/div[2]/div/div[2]/div/div[2]/div/div[1]/a/div[1]')
away = extract_text(d, '/html/body/div[1]/div/div[8]/div/div[2]/div/div[2]/div/div[2]/div/div[2]/div/div[1]/a/div[2]')

# get Scores by extracting text
home_score = extract_text('/html/body/div[1]/div/div[8]/div/div[2]/div/div[2]/div/div[2]/div/div[1]/div/span[1]')
away_score = extract_text('/html/body/div[1]/div/div[8]/div/div[2]/div/div[2]/div/div[2]/div/div[1]/div/span[2]')

print(f'{home} - {away}')
print(f'scores: {home_score} - {away_score}')

#excute bash commands inside python
execute_bash(f"echo '{home} - {away} ,scores: {home_score}:{away_score}' > ball.txt")

#want path of file
f_path=find_file('ball.txt')

sleep(1000)
