## Predicting Location in Atlanta, Georgia City Center: 
Data Science Competition 2019


You can use the [editor on GitHub](https://github.com/sammyburr/MMMFinalProject/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
import csv 
from datetime import datetime

with open('data_test.csv', "r") as srcfile:
	reader = csv.DictReader(srcfile)
	
	count = 0 
	entries = 0
	temp_traj = ''
	temp_target = ''
	hashes = []
	ids = []
	
	for row in reader: 
		if row['hash'] not in hashes:
			#t1 = datetime.strptime(row['time_entry'], "%H:%M:%S")
			#t2 = datetime.strptime(row['time_exit'], "%H:%M:%S")
			#totalt = t1-t2 
			ids.append(row)
			with open('results.csv', 'a', newline='') as outfile: 
				thewriter = csv.writer(outfile)
				thewriter.writerow([temp_traj, temp_target])
			if temp_target == 1:
				entries = entries + 1
			hashes.append(row['hash'])
			temp_traj = row['trajectory_id'] 
			count = count + 1
		
		else: 
			row_name, row_value = row['trajectory_id'].rsplit('_',1)
			temp_name, temp_value = temp_traj.rsplit('_', 1)
			if int(row_value) > int(temp_value):
				temp_traj = row['trajectory_id']
				if 3736901.4 <= float(row['x_entry']) and float(row['x_entry']) <= 3782901.4 and 19358905.4 >= float((row['y_entry'])[1:]) and float((row['y_entry'])[1:]) >= 19158905.4: 
					temp_target = 1
				else:
					temp_target = 0
				
print ('done')
print (count)
print (entries)

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/sammyburr/MMMFinalProject/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
