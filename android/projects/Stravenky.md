
### Stravenky

  

#### Refactoring notes (28.9.2020)

- naming
  - feature-XXXX
    - package naming: cz.myup.XXXX
  - rozdeleni projektu do 2 basic slozek, ktere budou rozdelovate featury pro partener app a customer app
	  - partner
	     - module naming
		     - partner-app
		     - feature-food-on-the-web
		     - feature-XXXX
	     - package-naming
		     - cz.myup.partner.xxxx
     - customer
	    - module naming
		    - customer-app
		    - feature-XXX
	    - package-naming
		   - cz.myup.customer.xxxx
		   
	  - shared - new shared module
		   - package-naming
			   - cz.myup.shared.xxx
	   - legacy-shared
			- package-naming
			   - cz.myup.legacy.shared.xxx
	   - vsechny nazvy, ktere budou se muset refaktorovat a byly by v kolizi z novymi -> predpona Legacy

- Coding
  - nepouzivat livedata ve VM - pouzivate vsude pouze flow - idealne inspirovat z nejnovejsi nejaktualne appky - beam-taxi-driver-an
    - https://github.com/MateeDevs/beam-taxi-driver-an/tree/feature/main_map
- Gradle 
  - predelat vsechny build.gradle -> build.gradle.kts - zatim klidne jenom u novych clean modulu