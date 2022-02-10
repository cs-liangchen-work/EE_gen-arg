# EE_gen-arg

复现 Document-Level Event Argument Extraction by Conditional Generation 这篇文章中自己感兴趣的点。

论文给出的github链接：https://github.com/raspberryice/gen-arg

模型输入：未填充的模板和上下文。   《s》  template 《s》《/s》document 《/s》

模型输出：填充好的模板。

利用生成的模板填充template中的arg参数。

![](https://github.com/cs-liangchen-work/EE_gen-arg/blob/main/picture/pic_1.png)


### 论文给出的代码的解释说明：
- model.py  模型  在这里选择是否进行那个有限制的。
```
if self.hparams.model=='gen':
    self.model = BartGen(self.config, self.tokenizer)
    self.model.resize_token_embeddings() 
elif self.hparams.model == 'constrained-gen':
    self.model = BartConstrainedGen(self.config, self.tokenizer)
    self.model.resize_token_embeddings() 
```
- network.py  没有限制的网络。
- constrained_gen.py  有限制的网络。
- convert_gen_to_output.py  生成的内容进行转化，是生成的string，而不是具体的内容。
