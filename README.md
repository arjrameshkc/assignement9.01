# assignement9.01


1.

petrol = LOAD 'petrol.txt' USING PigStorage(',') AS (dis_id:chararray, dis_name:chararray, buy_rate:chararray,sell_rate:chararray,vol_in:int,vol_out:int,year:int);
grpname = GROUP petrol by dis_name;
tot_sell = FOREACH grpname GENERATE group, SUM(petrol.vol_in);
dump tot_sell;

2. top_disid = FOREACH petrol GENERATE dis_id,(int)sell_rate * vol_in as sold_amt;
   top_10 = limit top_dispid 10;
   dump top_10;

3. grp1 = GROUP petrol by dis_name;
   cons = FOREACH grp1 GENERATE group, (Vol_in - vol_out) as consume; 
   vol_out = FOREACH cons GENERATE group, MAX(cons.consume);
   dump vol_out;


4. min_sell  =  ORDER petrol by sell_rate desc;
   limt_low =  limit min_sell 1;
   dump = limt_low;
