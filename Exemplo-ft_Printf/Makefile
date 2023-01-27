# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: ckunimur <ckunimur@student.42sp.org.br>    +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2023/01/20 21:22:41 by ckunimur          #+#    #+#              #
#    Updated: 2023/01/23 18:59:35 by ckunimur         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# Para entender a estrutura do Makefile vou usar como exemplo o arquivo Makefile da função ft_printf.c 
#Aqui as variaáveis são declaradas em caixa alta (NAME, CFLAGS)

NAME =	libftprintf.a 
# ALVO = biblioteca.a
#Ao executar o makefile, o objetivo é gerar uma arquivo, no caso -> libftprintf.a 
CFLAGS = -Wall\
		-Wextra\
		-Werror\
# CFLAGS são variaveis que irão executar um conjunto de comandos de a cordo com a regra
# No caso -Wall e demais são comandos de verificação 

AR = ar -rc
# AR é uma outra variável que também executa um conjunto de comandos
# ar -> comando para criar uma biblioteca de arquivos (.a)
# r  -> comando para adicionar arquivos ou substituir arquivos que tenham sido modificados na biblioteca
# c  -> quando um arquivo é criado é emitido uma mensagem de erro padrão, esse comando faz com que o novo arquivo seja criado silenciosamente

RM = rm -f

# rm -> comando para remover arquivos ou pastas
# -f -> tenta remover o arquivo sem precisar de um prompt de confirmação. Se a pasta não existir, não mostra nenhum aviso

SRCS =	ft_printf.c\
		ft_checkflag.c\
		ft_putchar.c\
		ft_puthexa.c\
		ft_putint.c\
		ft_putstr.c\
		ft_putunsigned.c\
		ft_putpointer.c

# SRCS nessa variável estão armazenados todos os arquivos fonte necessárias para executar o make

OBJS = $(SRCS:.c=.o)

# OBJS essa variável armazena os objetos que são gerados através dos arquivos fonte. É com eles que o make trabalha
# ela recebe uma cópia dos arquivos finte convertidos em objeto -> $(FONTE:.c=.o)

# all, clean, fclean e re são regras pré definidas do programa make

all:	$(NAME)
# all -> executado quando damos o comando make no terminal. all tem como dependencia o alvo

$(NAME): $(OBJS)
		$(AR) $(NAME) $(OBJS)
# (ALVO): tem dependencia dos objetos, que nesse momento serão criados e colocado dentro da variável $(OBJS)
#		$(COMANDO) -> gera $(ALVO) <- usando os arquivos $(OBJS)

clean: 			# esse comando não depende de nenhum outro arquivo, por isso o espaço em branco
	$(RM) $(OBJS)
#	$(COMANDO) -> executa em (OBJS)

fclean: clean 	# executa a função clean apagando os OBJS
	$(RM) $(NAME) 
# 	remove o ALVO

re: fclean all # executa a função fclean e a função make novamente

.PHONY: all clean fclean re
