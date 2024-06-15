1.
from collections import defaultdict

# Take input from the user for the votes
num_votes = int(input())
votes = [input() for _ in range(num_votes)]

# Create a dictionary to store the count of each candidate's votes
vote_count = defaultdict(int)

for candidate in votes:
    vote_count[candidate] += 1

max_votes = max(vote_count.values())

winners = [candidate for candidate, count in vote_count.items() if count == max_votes]

winner = min(winners)

print(winner)

2.
num_students = int(input())
student_data = {}

for _ in range(num_students):
    student_info = input().split()
    student_name = student_info[0]
    marks = list(map(int, student_info[1:]))
    student_data[student_name] = {
        'test_mark': marks[0],
        'assignment_mark': marks[1],
        'lab_mark': marks[2]
    }

average_scores = {name: sum(info.values()) / len(info) for name, info in student_data.items()}

max_average_score = max(average_scores.values())
highest_average_students = [name for name, score in average_scores.items() if score == max_average_score]

max_assignment_mark = max([info['assignment_mark'] for info in student_data.values()])
highest_assignment_students = [name for name, info in student_data.items() if info['assignment_mark'] == max_assignment_mark]

min_lab_mark = min([info['lab_mark'] for info in student_data.values()])
lowest_lab_students = [name for name, info in student_data.items() if info['lab_mark'] == min_lab_mark]

min_average_score = min(average_scores.values())
lowest_average_students = [name for name, score in average_scores.items() if score == min_average_score]

print(" ".join(highest_average_students))
print(" ".join(highest_assignment_students))
print(" ".join(sorted((lowest_lab_students))))
print(" ".join(lowest_average_students))

3.
letter_scores = {
    'A': 1, 'E': 1, 'I': 1, 'L': 1, 'N': 1, 'O': 1, 'R': 1, 'S': 1, 'T': 1, 'U': 1,
    'D': 2, 'G': 2,
    'B': 3, 'C': 3, 'M': 3, 'P': 3,
    'F': 4, 'H': 4, 'V': 4, 'W': 4, 'Y': 4,
    'K': 5,
    'J': 8, 'X': 8,
    'Q': 10, 'Z': 10
}

word = input().upper()

total_score = sum(letter_scores.get(letter, 0) for letter in word)

print("{} is worth {} points.".format(word, total_score))

4.
num_items = int(input())

test_dict = {}

for _ in range(num_items):
    key, *values = input().split()
    test_dict[key] = list(map(int, values))

sorted_dict = {k: sum(v) for k, v in sorted(test_dict.items(), key=lambda item: sum(item[1]))}

for key, value in sorted_dict.items():
    print(key, value)

5.
s1 = input()
s2 = input()

words_s1 = s1.split()
words_s2 = s2.split()

word_count = {}
for word in words_s1 + words_s2:
    word_count[word] = word_count.get(word, 0) + 1

uncommon_words = [word for word, count in word_count.items() if count == 1 and (word in words_s1 or word in words_s2)]

print(*uncommon_words)

