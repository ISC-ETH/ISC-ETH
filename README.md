# ETH-Contract

The world's leading technology, today's DAPP trend has arrived

# ABOUT ISC-ETH

Smart contracts were proposed by Nick Saab as early as the 1990s, and have not been practically applied due to the lack of a credible execution environment. After the emergence of blockchain technology, people discovered that blockchain is inherently capable of providing a trusted execution environment for smart contracts. Vitalik, the founder of Ethereum, first saw the integration of blockchain with smart contracts and blockchain, and released the world-leading technology of "Ethereum: the next generation of smart contracts and decentralized application platforms." Today's DAPP trend has arrived Unstoppable, it will create a new wave of wealth system worldwide!

About the ISC-ETH Global Smart Contract International Smart Contract for Ethereum "ISCE project for short" is a smart contract developed based on the bottom of the Ethereum public chain. The ISC-ETH contract is the only DAPP technology application created by many technical teams of the Ethereum founder .It is also the only contract-based income DAPP application in the world. Both income and output are built on the trust public chain. It is the only DAPP application based on the ETH public chain. It is also the world's only contract-based revenue platform It has solved the trust relationship between investors and the platform, and has adopted an electronic contract that cannot be tampered with. This will be a new revolutionary financial market for global blockchains.

# Contract Profit Source

The project platform comes from multiple sources of income. Futures leveraged contracts participate in Ethereum's futures trading and receive fixed income. When we invest in community contracts, we cannot use them all as nodes, because the profits of the nodes are not enough for us to share. Currently, most of the funds will be used for arbitrage transactions. For example, when US $ 248 is sold, there will be 10,000 ETH, which is US $ 2.48 million; when US $ 218 is retrieved, 2.48 million yuan = 11.3 million ETH, and the net profit will be 130 ETH. . As long as the market rises and falls, there must be margin. Once you have a profit, you must have a profit in English. With many chips, you can use the adverbial clause: smashing and pulling. In the smashing adverbial clause: between pulling, you can naturally earn ETH. We invest in global nodes in the super node award contract. At the same time, the platform uses global Ethereum entertaining quiz games to make more Ethereum nodes active, thereby improving the actual application of Ethereum. Of course, we can also let Ethereum participate in the game and bring entertainment to everyone, thanks to the participation of players worldwide!

# Contract revenue

The platform adopts the rules of the game in global booking, order acquisition and control modes. The platform pays deposits first, then orders for all players and makes balance payments, and then pays deposits 7 days later to reward the last round of principals and points. 7% per principal plus interest. Successfully registered as a star member, you can enjoy 50% of the direct recommendation income of this generation! For example, if you recommend me, I can earn 30 eth per month and you can earn 15 eth per month. If you recommend 100 people, the first generation will get 1500 eth per month. Eth times the real-time price of the exchange is your actual return. The replacement of star members requires conditions. Direct promotion requires the promotion of 3 effective members, 10 effective members of the umbrella team, and enjoys 20% of the second-generation income. After two stars, it is easy to earn 20-60 eth per month. Samsung membership requires conditions. Three of the directly recommended members are two-star members, which will cover Samsung members. Samsung members enjoy 10% of third-generation income. Under the four-star standard condition, four two-star members are directly recommended to directly meet the standard of four-level members. Four Stars enjoys 2% of fourth-generation income. According to the five-star standard conditions, five two-star members are directly recommended as five-star members. Five-star members can enjoy 2% of fourth-generation income, and can enjoy 2% of income without limit. The final six-star evaluation criteria is that I am a five-star member, and one of my team directly promoted to a five-star member will reach the level of six-star. In addition to enjoying 50% of the first generation, 20% of the second generation, 10% of the third generation, 2% of the fourth generation and 2% of the unlimited generation. It will reward you again with 60 eth global dividends, while enjoying 1% global smart dividends.

# Part of code

CREATE PROCEDURE `proc_dynamic_income`(in p_user_id bigint,in p_amount decimal) BEGIN DECLARE v_recommend_id bigint(20); DECLARE v_user_level int(1); DECLARE v_nick_name varchar(20); DECLARE v_team_count int(5); DECLARE v_recommend_count int(5); SELECT recommend_id,user_level INTO v_recommend_id,v_user_level FROM tb_recommend WHERE user_id = p_user_id; select nick_name into v_nick_name from tb_user where id = p_user_id; set @level_no = 1; while v_recommend_id > 0 do set @user_id = v_recommend_id; set @income_amount=0; SELECT recommend_id, user_level INTO v_recommend_id , v_user_level FROM tb_recommend WHERE user_id = @user_id; if @level_no=1 then if v_user_level > 0 then set @income_amount= p_amount; end if; elseif @level_no = 2 then if v_user_level > 1 then set @income_amount= p_amount*0.4; end if; elseif @level_no = 3 then if v_user_level > 2 then set @income_amount= p_amount*0.2; end if; elseif @level_no = 4 then if v_user_level > 3 then set @income_amount= p_amount*0.02; end if; else if v_user_level > 4 then set @income_amount= p_amount*0.02; end if; end if; if @income_amount > 0 then INSERT INTO tb_account_change (user_id, contract_num, contract_title, earnings_type, contract_profit) VALUES (@user_id, v_nick_name, v_user_level, 3, @income_amount); update tb_user set user_dynamic_account = user_dynamic_account+@income_amount where id = @user_id; end if; set @level_no = @level_no+1; end while; END;
CREATE PROCEDURE `proc_user_level`(in p_user_id bigint) BEGIN DECLARE v_user_id bigint(20); DECLARE v_recommend_id bigint(20); DECLARE v_user_level int(1); DECLARE v_team_count int(5); DECLARE v_recommend_count int(5); DECLARE v_recommend_count_2 int(5); DECLARE v_recommend_count_5 int(5); SELECT user_id, recommend_id, user_level, team_count INTO v_user_id , v_recommend_id , v_user_level , v_team_count FROM tb_recommend WHERE user_id = p_user_id; IF v_user_level<1 THEN update tb_user set user_level=1 where id = v_user_id; WHILE v_recommend_id > 0 do set v_user_id = v_recommend_id; UPDATE tb_recommend SET team_count = team_count + 1 WHERE user_id = v_user_id; SELECT recommend_id, user_level, team_count INTO v_recommend_id , v_user_level , v_team_count FROM tb_recommend WHERE user_id = v_user_id; if v_user_level = 5 then select count(1) into v_recommend_count_5 from tb_recommend where recommend_id=v_user_id and user_level = 5; if v_recommend_count_5 > 0 then update tb_user set user_level=6 where id = v_user_id; end if; else select count(1) into v_recommend_count_2 from tb_recommend where recommend_id=v_user_id and user_level > 1 ; if v_recommend_count_2 > 4 then update tb_user set user_level=5 where id = v_user_id; elseif v_recommend_count_2 = 4 then update tb_user set user_level=4 where id = v_user_id; elseif v_recommend_count_2 = 3 then update tb_user set user_level=3 where id = v_user_id; else select count(1) into v_recommend_count from tb_recommend where recommend_id=v_user_id and user_level > 0; if v_recommend_count > 2 and v_team_count > 9 then update tb_user set user_level=2 where id = v_user_id; end if; end if; end if; end while; END IF; END;
