import time
from bs4 import BeautifulSoup
import requests

print('Enter some skills you not familiar with')
unfamiliar_skills = input('>')
print(f'Filitering out {unfamiliar_skills}')

def find_jobs():
    html_text = requests.get('https://useme.com/pl/jobs/category/programowanie-i-IT,2/?').text
    soup = BeautifulSoup(html_text, 'lxml')
    jobs = soup.find_all('div', class_='job')

    for index, job in enumerate (jobs):
        budget = job.find('span', class_ = 'job__budget-value').text.replace(' ', '')

        if 'Donegocjacji' not in  budget:

            skills = job.find('div', class_ = 'job__skills').text.strip().replace('\n', ', ')
            data = job.find('div', 'job__header-details job__header-details--offers').text.strip().replace('\n', ', ')
            more_info = job.div.h2.a['href']

            if unfamiliar_skills not in skills:
                with open(f'jobs/{index}.txt', 'w') as f:
                    f.write(f"Budget:  {budget.strip()} \n")
                    f.write(f"Requiered skills:  {skills.strip()} \n")
                    f.write(f"Recruiters:  {data.strip()} \n")
                    f.write(f"Header:  useme.com{more_info} \n")
                print(f'File saved: {index}')

if __name__ == '__main__':
    while True:
        find_jobs()
        time_wait = 10
        print(f"Waiting {time_wait} minutes...")
        time.sleep(time_wait * 60)
