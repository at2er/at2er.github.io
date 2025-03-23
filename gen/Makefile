GEN_INDEX = ./gen_index
GEN_POST = ./gen_post

POSTS_DIR = posts
POSTS_SRC = $(wildcard $(POSTS_DIR)/*.md)
POSTS_TARGET_DIR = ../posts
POSTS = $(addprefix ../,$(POSTS_SRC:.md=.html))
INDEX = ../index.html
INDEX_POSTS = $(foreach file,$(POSTS_SRC:.md=.html),\
	$(file):$(basename $(notdir $(file))))

$(INDEX): $(GEN_INDEX) $(GEN_POST) $(POSTS)
	$(GEN_INDEX) $(INDEX_POSTS) > $(INDEX)

$(POSTS_TARGET_DIR)/%.html: $(POSTS_DIR)/%.md $(GEN_POST)
	$(GEN_POST) $(basename $(notdir $<)) $< > $@

.PHONY: all index posts $(INDEX) $(POSTS)
index: $(INDEX)
posts: $(POSTS) $(POSTS_SRC)
all: index posts
