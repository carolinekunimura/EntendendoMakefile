# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: ckunimur <ckunimur@student.42sp.org.br>    +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2023/01/23 18:44:21 by ckunimur          #+#    #+#              #
#    Updated: 2023/01/27 19:07:57 by ckunimur         ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

# Para entender a estrutura do Makefile vou usar como exemplo o arquivo da minilibX .
# Aqui as variáveis são declaradas em caixa alta (NAME, CFLAGS).
# As explicações dos comandos são explicações simples sobre a aplicação no script, consulte o manual para obter mais informações.

INC	=%%%% 
# VARIÁVEL  % todos os arquivos (equivalente a '*').

UNAME = $(shell uname) 
# ALVO = $(função argumento).
# Vai ser gerado um arquivo da função shell com o argumento uname.
# uname -> comando que exibe os dados do sistema.

CC	= gcc # CC é a varável do comando de compilação.
ifeq ($(UNAME),FreeBSD) # ifeq -> funciona como 'if' determinando qual linha de comando será executada.
	CC = clang 
# CC -> váriavel que recebe o comando de compilação clang .
endif # encerra a condição ifeq .

NAME		= libmlx.a
# ALVO = biblioteca.a
NAME_UNAME	= libmlx_$(UNAME).a
# ALVO = biblioteca_$(VARIÁVEL).a

SRC	= mlx_init.c mlx_new_window.c mlx_pixel_put.c mlx_loop.c \ # VARIAVEL = arquivos fonte.c
	mlx_mouse_hook.c mlx_key_hook.c mlx_expose_hook.c mlx_loop_hook.c \
	mlx_int_anti_resize_win.c mlx_int_do_nothing.c \
	mlx_int_wait_first_expose.c mlx_int_get_visual.c \
	mlx_flush_event.c mlx_string_put.c mlx_set_font.c \
	mlx_new_image.c mlx_get_data_addr.c \
	mlx_put_image_to_window.c mlx_get_color_value.c mlx_clear_window.c \
	mlx_xpm.c mlx_int_str_to_wordtab.c mlx_destroy_window.c \
	mlx_int_param_event.c mlx_int_set_win_event_mask.c mlx_hook.c \
	mlx_rgb.c mlx_destroy_image.c mlx_mouse.c mlx_screen_size.c \
	mlx_destroy_display.c


OBJ_DIR = obj # Essa variável será usada como referencia para adicionar um prefixo no momento de criação dos arquivo .o (objeto)
OBJ	= $(addprefix $(OBJ_DIR)/,$(SRC:%.c=%.o)) # OBJS essa variável armazena os objetos que são gerados através dos arquivos fonte.c . É com eles que o make trabalha.
# VARIAVEL = $(comando $(variavel)/, $(comando que converte a fonte(.c) em objeto(.o))
CFLAGS	= -O3 -I$(INC) 
# VARIÁVEL = comandos$(VARIAVEL)
# -O3 -> otimizador para o código executar mais rápido
# -I -> Especifica em qual pasta procurar o(s) Makefile(s) no caso a varável $(INC)

# all, clean, fclean e re são regras pré definidas do programa make

all	: $(NAME) # all -> executado quando damos o comando make no terminal. all tem como dependencia o alvo

$(OBJ_DIR)/%.o: %.c #
	@mkdir -p $(OBJ_DIR)
	$(CC) $(CFLAGS) $(IFLAGS) -c $< -o $@

$(NAME)	: $(OBJ) # (ALVO): tem dependencia dos objetos, que nesse momento serão criados e colocados dentro da variável $(OBJS)
	ar -r $(NAME) $(OBJ)
#	comando -> gera $(ALVO) <- usando os arquivos $(OBJS)
# ar -> comando para compilar criar uma biblioteca de arquivos (.a)
# r  -> comando para adicionar arquivos ou substitui arquivos que tenham sido modificados na biblioteca (no caso de um remake)
	ranlib $(NAME)
	cp $(NAME) $(NAME_UNAME)
# c -> quando um arquivo é criado é emitido uma mensagem de  execução, esse comando faz com que o novo arquivo seja criado silenciosamente, sem notificação.
# p -> grava o conteúdo dos arquivos compactados especificados na saída padrão. Se nenhum arquivo for especificado, o conteúdo de todos os arquivos no arquivo será gravado na ordem em que aparecem no arquivo.
check: all
	@test/run_tests.sh

show: # função pre definida executa o comando de printar na telas as informções obtidas nas flags
	@printf "NAME  		: $(NAME)\n"
	@printf "NAME_UNAME	: $(NAME_UNAME)\n"
	@printf "CC		: $(CC)\n"
	@printf "CFLAGS		: $(CFLAGS)\n"
	@printf "SRC		:\n	$(SRC)\n"
	@printf "OBJ		:\n	$(OBJ)\n"
# @ -> silencia msg padrão de execução do shell. 
	
clean	:			# esse comando não depende de nenhum outro arquivo, por isso o espaço em branco
	rm -rf $(OBJ_DIR)/ $(NAME) $(NAME_UNAME) *~ core *.core
#	comando $(VARIAVEL)/ -> executa em (OBJS)

.PHONY: check show clean
# .PHONY faz com que que os comandos definidos aqui sejam executados prioritariamente caso exista algum outro arquivo com mesmo nome. 