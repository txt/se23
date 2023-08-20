MAKEFLAGS += --silent

help : Makefile ## print help
	echo ""; printf "usage: make [OPTIONS]\n\n"
	@awk 'BEGIN {FS="[ \t]*:.*##[ \t]*"}  \
	  NF==2 { printf \
           "  \033[36m%-25s\033[0m %s\n","make " $$1,$$2}'  $< \
	| grep -v awk

all: ../LICENSE.md $(shell ls *.md) ## for all *.md, update from /README.md 

ONE=cat $< | awk 'BEGIN {FS="\n";RS=""} {print $$0 "\n"; exit}' | awk '{print "  " $$0} END{print("\n\n")}' 
TWOPLUS=cat $@ | awk 'BEGIN {FS="\n";RS=""} NR==1 { print("\n\n"); next} {print $$0 "\n\n"}'

pub: ## save all to Github
	$(MAKE) all
	git add *;git commit -am save;git push;git status

../LICENSE.md: ../README.md Makefile ## update license
	 @echo "$@ ... " ; ($(ONE);  $(TWOPLUS)) > .tmp; mv .tmp $@

*.md: ../README.md Makefile
	echo "$@ ... " 
	@($(ONE);  $(TWOPLUS)) > .tmp; mv .tmp $@



