Git checkout vs git switch 

 

    Git checkout 

La commande “git checkout” permet la bascule sur une autre branche ou de restaurer des fichiers de l’arbre actuel. 

Il existe deux commandes principales pour ces actions : 

    “git checkout <branchname>” pour basculer d’une branche à une autre. 

    “git checkout –b <branchname>" pour créer une branche et basculer dessus. 

    “git checkout -- <path_to_file>” pour restaurer un ou plusieurs fichiers qui ne sont pas staged sans changer de branche. 

 

    Git switch et git restore 

Git a introduit deux nouvelles commandes lors de la maj 2.23 : 

    “git switch” pour basculer d’une branche à une autre. 

    “git switch <branchname> pour basculer sur une branche existante. 

    “git switch -c <branchname> pour créer une nouvelle branche et basculer dessus. 

    “git switch -” pour revenir sur la branche extraite précédemment. 

    “git restore” pour restaurer un ou plusieurs fichiers. 

    “git restore --source" pour spécifier ce que l’on veut copier.  

    “git restore --stage" et “git restore --worktree" pour spécifier la destination. 

 

    Pourquoi avoir implanté git switch alors que git checkout le faisait déjà ? 

Les commandes “git checkout <branchname> et ” “git checkout -- <path_to_file>” avaient tendance à rendre confus les utilisateurs, aussi bien les novices que les plus expérimentés, car ces deux fonctionnalités sont totalement différentes, notamment si l’on travaille sur un fichier et une branche du même nom. 

 

 

 

 

 

 

Pour remédier à cela et rendre les commandes plus claires et concises sur l’interface, Git a donc introduit le 16 aout 2019 les commandes “git switch” et “git restore”. La commande “git checkout” était considérée trop “couteau suisse” avec des sous commandes sans rapports. 

 

Voici un tableau comparatif des commandes “git checkout” et “git switch" 

previous command 
	

new command 

git checkout <branch> 
	

git switch <branch> 

git checkout 
	

N/A (use git status) 

git checkout -b <new_branch> [<start_point>] 
	

git switch -c <new-branch> [<start-point>] 

git checkout -B <new_branch> [<start_point>] 
	

git switch -C <new-branch> [<start-point>] 

git checkout --orphan <new_branch> 
	

git switch --orphan <new-branch> 

git checkout --orphan <new_branch> <start_point> 
	

N/A (use git switch <start-point> then git switch --orphan <new-branch>) 

git checkout [--detach] <commit> 
	

git switch --detach <commit> 

git checkout --detach [<branch>] 
	

git switch --detach [<branch>] 

git checkout [--] <pathspec>… 
	

git restore [--] <pathspec>… 

git checkout --pathspec-from-file=<file> 
	

git restore --pathspec-from-file=<file> 

git checkout <tree-ish> [--] <pathspec>… 
	

git restore -s <tree> [--] <pathspec>… 

git checkout <tree-ish> --pathspec-from-file=<file> 
	

git restore -s <tree> --pathspec-from-file=<file> 

git checkout -p [<tree-ish>] [--] [<pathspec>…] 
	

git restore -p [-s <tree>] [--] [<pathspec>…] 

 

 

 

 

 

Sources 

https://github.blog/2019-08-16-highlights-from-git-2-23/ 

https://www.infoq.com/news/2019/08/git-2-23-switch-restore/ 

https://stackoverflow.com/questions/57265785/whats-the-difference-between-git-switch-and-git-checkout-branch 

https://www.scaler.com/topics/git/git-switch-vs-checkout/ 