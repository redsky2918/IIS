# Intelligent Information Systems, Assessment 2 (Jason Program)

## 1. List of versions (3 variations of the Jason project)

### asseMSc_1

* asseMSc_1.mas2j
* applicant_1_agent.asl
* applicant_2_agent.asl
* assessor_agent.asl

### asseMSc_2

* asseMSc_2.mas2j
* applicant_1_agent.asl
* applicant_2_agent.asl
* assessor_agent.asl

### asseMSc_3

* asseMSc_3.mas2j
* applicant_1_agent.asl
* applicant_2_agent.asl
* assessor_agent.asl

## 2. Scenario for each version

### asseMSc_1	
* There are cureently two applicants.
	* Applicant 1 (David) -> an upper second-class honours degree AND 1 year work experience
	```shell
	undergraduate_module_marks(1, 60).
	undergraduate_module_marks(1, 60).
	undergraduate_module_marks(1, 60).

	workExperience(1,0).
	workExperience(2,1).
	
	undergraduate_award(2,1) :- 
	undergraduate_module_marks(1, X) & undergraduate_module_marks(2, Y) & undergraduate_module_marks(3, Z) 
	& ((X + Y + Z)/3 < 70) & ((X + Y + Z)/3 >= 60).
	
	no_work_experience :- workExperience(1,X) & workExperience(2,Y) & (X + Y < 2).
	```

	* Applicant 2 (Alice) -> an lower second-class honours degree AND 1 year work experience
	```shell
	undergraduate_module_marks(1, 50).
	undergraduate_module_marks(2, 50).
	undergraduate_module_marks(3, 50).
	
	workExperience(1,0).
	workExperience(2,1).

	undergraduate_award(2,2) :- 
	undergraduate_module_marks(1, X) & undergraduate_module_marks(2, Y) & undergraduate_module_marks(3, Z) 
	& ((X + Y + Z)/3 < 60) & ((X + Y + Z)/3 >= 50).
	
	no_work_experience :- workExperience(1,X) & workExperience(2,Y) & (X + Y < 2).
	```
* The course vacancy
	* Two vacancies (in assessor_agent.asl)
	```shel
	vacancy(2).
	```
* Scenario
	* There are currently two vacancies for the course.
	* Applicant 1 (David) can study at the course as his academic qualification and work experience satisfy the entry requirements.
	* Applicant 2 (Alice)  cannot study at the course as her academic qualification and work experience does not satisfy the entry requirements.
	* The assesor agent has to offer Applicant 1 (David) one of the two vacancies.
	* The assesor agent has to not offer Applicant 2 (Alice) one of the two vacancies.
		
### asseMSc_2
* There are cureently two applicants.
	* Applicant 1 -> an upper second-class honours degree AND 1 year work experience
	```shell
	undergraduate_module_marks(1, 60).
	undergraduate_module_marks(2, 60).
	undergraduate_module_marks(3, 60).
	
	workExperience(1,0).
	workExperience(2,1).

	undergraduate_award(2,1) :- 
	undergraduate_module_marks(1, X) & undergraduate_module_marks(2, Y) & undergraduate_module_marks(3, Z) 
	& ((X + Y + Z)/3 < 70) & ((X + Y + Z)/3 >= 60).

	no_work_experience :- workExperience(1,X) & workExperience(2,Y) & (X + Y < 2).
	```

	* Applicant 2 -> an upper second-class honours degree AND 2 year work experience
	```shell
	undergraduate_module_marks(1, 60).
	undergraduate_module_marks(2, 60).
	undergraduate_module_marks(3, 60).

	workExperience(1,1).
	workExperience(2,1).

	undergraduate_award(2,1) :- 
	undergraduate_module_marks(1, X) & undergraduate_module_marks(2, Y) & undergraduate_module_marks(3, Z) 
	& ((X + Y + Z)/3 < 70) & ((X + Y + Z)/3 >= 60).

	have_work_experience :- workExperience(1,X) & workExperience(2,Y) & (X + Y >= 2).
	```
* The course vacancy
	* Two vacancies (in assessor_agent.asl)
	```shell
	vacancy(2).
	```
* Scenario
	* There are currently two vacancies for the course.
	* Applicant 1 (David) can study at the course as his academic qualification and work experience satisfy the entry requirements.
	* Applicant 2 (Alice)  can study at the course as his academic qualification and work experience satisfy the entry requirements.
	* The assesor agent has to offer Applicant 1 (David) one of the two vacancies.
	* The assesor agent has to offer Applicant 2 (Alice) one of the two vacancies.

### asseMSc_3
* There are cureently two applicants.
	* Applicant 1 -> an upper second-class honours degree AND 2 year work experience
	```shell
	undergraduate_module_marks(1, 60).
	undergraduate_module_marks(2, 60).
	undergraduate_module_marks(3, 60).
	
	workExperience(1,1).
	workExperience(2,1).

	undergraduate_award(2,1) :- 
	undergraduate_module_marks(1, X) & undergraduate_module_marks(2, Y) & undergraduate_module_marks(3, Z) 
	& ((X + Y + Z)/3 < 70) & ((X + Y + Z)/3 >= 60).
	
	have_work_experience :- workExperience(1,X) & workExperience(2,Y) & (X + Y >= 2).
	```

	* Applicant 2 -> an upper second-class honours degree AND 2 year work experience
	```shell
	undergraduate_module_marks(1, 60).
	undergraduate_module_marks(2, 60).
	undergraduate_module_marks(3, 60).
	
	workExperience(1,1).
	workExperience(2,1).

	undergraduate_award(2,1) :- 
	undergraduate_module_marks(1, X) & undergraduate_module_marks(2, Y) & undergraduate_module_marks(3, Z) 
	& ((X + Y + Z)/3 < 70) & ((X + Y + Z)/3 >= 60).

	have_work_experience :- workExperience(1,X) & workExperience(2,Y) & (X + Y >= 2).
	```
* The course vacancy 
	* One vacancy (in assessor_agent.asl)
	```shell
	vacancy(1).
	```
* Scenario
	* There is currently only one vacancy for the course.
	* Applicant 1 (David) can study at the course as his academic qualification and work experience satisfy the entry requirements.
	* Applicant 2 (Alice)  can study at the course as his academic qualification and work experience satisfy the entry requirements.
	* The assesor agent has to only offer one applicant who has finished his/her application eariler than the other since there is only one vacancy.

## 3. Key Jason features of each asl file

### Applicant agent (applicant_1_agent & applicant_2_agent)

| Feature of Jason | Type | Key sub actions when triggered | Description |
| --- | --- | --- | --- |
| `!requestApplication(bristol)` | Initial achievement goal |  |  |
| `+!requestApplication(X) : lookingForCourse(uni)` | Goal addition triggering event | `!checkVacancy` | |
| `+!requestApplication(X) : not lookingForCourse(uni)` | Goal addition triggering event |  |  |
| `+!checkVacancy : true` | Sub goal addition triggering event  | `.send(Y, tell, checkingVacancy(X))` | The agent requests the assessor agent to check whether there is a vacancy for the course |
| `+!sendInfo : undergraduate_award(A,B) & have_work_experience & A + B <= 3` | Sub goal addition triggering event with plan context with conjunctions | `.send(Y, tell, good_award_workExp(A,B))` | The agent sends its academic award and existence of work experience |
| `+!sendInfo : undergraduate_award(A,B) & no_work_experience & A + B <= 3` | Sub goal addition triggering event with plan context with conjunctions | `.send(Y, tell, good_award_no_workExp(A,B))` | The agent sends its academic award and existence of work experience |
| `+!sendInfo : undergraduate_award(A,B) & have_work_experience & A + B > 3` | Sub goal addition triggering event with plan context with conjunctions | `.send(Y, tell, bad_award_workExp(A,B))` | The agent sends its academic award and existence of work experience |
| `+!sendInfo : undergraduate_award(A,B) & no_work_experience & A + B > 3` | Sub goal addition triggering event with plan context with conjunctions | `.send(Y, tell, bad_award_no_workExp(A,B))` | The agent sends its academic award and existence of work experience |
| `+vacancy_available(X)[source(Y)] : true` | Belief change triggering event | `!sendInfo` | |
| `+vacancy_not_available(X)[source(Y)] : true` | Belief change triggering event | `!requestApplication(X)` | |
| `+confirm[source(Y)]: true` | Belief change triggering event | `.send(Y, tell, final_decision)` | |
| `+receiveInvitation[source(Y)]: true` | Belief change triggering event | `-lookingForCourse(U)` | |
| `+rejected[source(Y)]: true` | Belief change triggering event | | |

### Assesor agent (assessor_agent)

| Feature of Jason | Type | Key sub actions when triggered | Description |
| --- | --- | --- | --- |
| `!vacancyAvailable` | Initial achievement goal | | |
| `+!vacancyAvailable : vacancy(N) = 0` | Goal addition triggering event with a plan context | | |
| `+!vacancyAvailable : true` | Goal addition triggering event | | |
| `+checkingVacancy(X)[source(Y)] : vacancy(N) = 0` | Belief change triggering event with a plan context | `.send(Y, tell, vacancy_not_available(Y))` | The agent informs the applicant agent that there is no vacancy for the course |
| `+checkingVacancy(X)[source(Y)] : true` | Belief change triggering event | `.send(Y, tell, vacancy_available(Y))` | The agent informs the applicant agent that there are vacancies for the course |
| `+good_award_workExp(A,B)[source(Y)] : true` | Belief change triggering event | `.send(Y, tell, confirm)` | |
| `+good_award_no_workExp(A,B)[source(Y)] : true` | Belief change triggering event | `.send(Y, tell, confirm)` | |
| `+bad_award_workExp(A,B)[source(Y)]: true` | Belief change triggering event | `.send(Y, tell, confirm)` | |
| `+bad_award_no_workExp(A,B)[source(Y)]: true` | Belief change triggering event | `.send(Y, tell, rejected)` | |
| `+final_decision[source(Y)] : (vacancy(N) & N < 1) or no_vacancy` | Belief change triggering event with plan contexts | `.send(Y, tell, rejected)` | The agent informs the result of the admission process |
| `+final_decision[source(Y)] : vacancy(N) & N > 0` | Belief change triggering event with plan contexts | `?vacancy(N); ?uni(X); W = N - 1;` | The agent updates the number of vacancies for the course |
| | | `-vacancy(N); +vacancy(W);` | The agent updates the initial belief vacancy(N) by vacancy(W), deducting 1 place from the number of vacancies stated earlier, as an applicant has been offered |
| | | `.send(Y, tell, receiveInvitation)` | The agent informs the result of the admission process |

## 4. Results

| Subject | Object | Action | Description |
| --- | --- | --- | --- |
| assessor_agent | aplicant_1_agent or aplicant_2_agent | `.send(Y, tell, vacancy_not_available(Y)).` | Currently, the assessor agent has closed the admission system as there is no vacancy |
| assessor_agent | aplicant_1_agent or aplicant_2_agent | `.send(Y, tell, receiveInvitation)` | The applicant has passed all the entry requirements, and there is a vacancy for the course |
| assessor_agent | aplicant_1_agent or aplicant_2_agent | `.send(Y, tell, rejected)` | The applicant has not passed the entry requirements, OR the applicant has passed all the entry requirements, but there is no vacancy |

## 5. Further notices on the Jason project

* The scenario of asseMSc_3 is that even though the two applicants satisfy the entry requirements, only one of the two applicants who passes the system earlier than the other applicant will be offered by the jason program since there is only one vacancy for the course. One of the two applicants should received `.print("I am very sorry ", Y, ". We have found all studendts for this course"); .send(Y, tell, rejected)` and the other should received `.print("Congratuation! ", Y, ". You can !!UNCONDITIONALLY!! study at University of ", X, "."); .send(Y, tell, receiveInvitation)`. 
However, there are two possible executions of the same Jason project; one is the intended execution, and the other is both applicants can study at the cousre even though there is only one vacancy. The latter case means both the applicant agents receive `.print("Congratuation! ", Y, ". You can !!UNCONDITIONALLY!! study at University of ", X, "."); .send(Y, tell, receiveInvitation)`. These two execution results are randomly observed.

