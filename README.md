Download Link: https://assignmentchef.com/product/solved-csis-312-assignment-3-payroll-system
<br>
<header class="entry-header">

 <p class="entry-title">Modify the payroll system of Figs. 10.4–10.9 to include an additional Employee subclass PieceWorker that represents an employee whose pay is based on the number of pieces of merchandise produced.

</header>

5/5 - (1 vote)

Class PieceWorker should contain private instance variables wage (to store the employee’s wage per piece) and pieces (to store the number of pieces produced).

Provide a concrete implementation of method earnings in class PieceWorker that calculates the employee’s earnings by multiplying the number of pieces produced by the wage per piece.

Create an array of Employee variables to store references to objects of each concrete class in the new Employee hierarchy (SalariedEmployee, CommissionEmployee, HourlyEmployee, BasePlusCommissionEmployee, and now PieceWorker).

For each Employee, display its String representation and earnings.

Submit this assignment by 11:59 p.m. (ET) on Monday of Module/Week 3.



<center>

 <img decoding="async" alt="BMIS 312" width="696" height="239" data-src="https://i1.wp.com/www.homework24h.com/wp-content/uploads/2016/05/uml-diagram.jpg?w=895&amp;ssl=1" class="lazyload" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==">

 <noscript>

  <img decoding="async" src="https://i1.wp.com/www.homework24h.com/wp-content/uploads/2016/05/uml-diagram.jpg?w=895&amp;ssl=1" alt="BMIS 312" width="696" height="239">

 </noscript>

</center>

<table border="0" cellspacing="0" cellpadding="0">

 <tbody>

  <tr>

   <td class="gutter"></td>

   <td class="code"></td>

  </tr>

 </tbody>

</table>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

33

34

35

36

37

38

39

40

41

42

43

44

45

46

47

48

49

50

51

52

53

54

55

56

57

58

59

60

61

62

63

64

65

66

67

68

69

70

71

72

73

74

75

76

77

78

79

80

81

82

83

84

85

86

87

88

89

90

91

92

93

94

95

96

97

98

99

100

101

102

103

104

105

106

107

108

109

110

111

112

113

114

115

116

117

118

119

120

121

122

123

124

125

126

127

128

129

130

131

132

133

134

135

136

137

138

139

140

141

142

143

144

145

146

147

148

149

150

151

152

153

154

155

156

157

158

159

160

161

162

163

164

165

166

167

168

169

170

171

172

173

174

175

176

177

178

179

180

181

182

183

184

185

186

187

188

189

190

191

192

193

194

195

196

197

198

199

200

201

202

203

204

205

206

207

208

209

210

211

212

213

214

215

216

217

218

219

220

221

222

223

224

225

226

227

228

229

230

231

232

233

234

235

236

237

238

239

240

241

242

243

244

245

246

247

248

249

250

251

252

253

254

255

256

257

258

259

260

261

262

263

264

265

266

267

268

269

270

271

272

273

274

275

276

277

278

279

280

281

282

283

284

285

286

287

288

289

290

291

292

293

294

295

296

297

298

299

300

301

302

303

304

305

306

307

308

309

310

311

312

313

314

315

316

317

318

319

320

321

322

323

324

325

326

327

328

329

330

331

332

333

334

335

336

337

338

339

340

341

342

343

344

345

346

347

348

349

350

351

352

353

354

355

356

357

358

359

360

361

362

363

364

365

366

367

368

369

370

371

372

373

374

<code class="php comments">// Fig. 10.7: CommissionEmployee.java</code>

<code class="php comments">// CommissionEmployee class extends Employee.</code>

<code class="php keyword">public</code> <code class="php keyword">class</code> <code class="php plain">CommissionEmployee </code><code class="php keyword">extends</code> <code class="php plain">Employee </code>

<code class="php plain">{</code>

<code class="php spaces">   </code><code class="php keyword">private</code> <code class="php plain">double grossSales; </code><code class="php comments">// gross weekly sales</code>

<code class="php spaces">   </code><code class="php keyword">private</code> <code class="php plain">double commissionRate; </code><code class="php comments">// commission percentage</code>

<code class="php spaces">   </code><code class="php comments">// constructor</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">CommissionEmployee(String firstName, String lastName, </code>

<code class="php spaces">      </code><code class="php plain">String socialSecurityNumber, double grossSales, </code>

<code class="php spaces">      </code><code class="php plain">double commissionRate)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php plain">super(firstName, lastName, socialSecurityNumber);</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(commissionRate &lt;= 0.0 || commissionRate &gt;= 1.0) </code><code class="php comments">// validate </code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code>

<code class="php spaces">            </code><code class="php string">"Commission rate must be &gt; 0.0 and &lt; 1.0"</code><code class="php plain">);</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(grossSales &lt; 0.0) </code><code class="php comments">// validate</code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code><code class="php string">"Gross sales must be &gt;= 0.0"</code><code class="php plain">);</code>

<code class="php spaces">      </code><code class="php plain">this.grossSales = grossSales;</code>

<code class="php spaces">      </code><code class="php plain">this.commissionRate = commissionRate;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// set gross sales amount</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">void setGrossSales(double grossSales)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(grossSales &lt; 0.0) </code><code class="php comments">// validate</code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code><code class="php string">"Gross sales must be &gt;= 0.0"</code><code class="php plain">);</code>

<code class="php spaces">      </code><code class="php plain">this.grossSales = grossSales;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return gross sales amount</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">double getGrossSales()</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">grossSales;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// set commission rate</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">void setCommissionRate(double commissionRate)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(commissionRate &lt;= 0.0 || commissionRate &gt;= 1.0) </code><code class="php comments">// validate</code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code>

<code class="php spaces">            </code><code class="php string">"Commission rate must be &gt; 0.0 and &lt; 1.0"</code><code class="php plain">);</code>

<code class="php spaces">      </code><code class="php plain">this.commissionRate = commissionRate;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return commission rate</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">double getCommissionRate()</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">commissionRate;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// calculate earnings; override abstract method earnings in Employee</code>

<code class="php spaces">   </code><code class="php plain">@Override                                                           </code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">double earnings()                                            </code>

<code class="php spaces">   </code><code class="php plain">{                                                                   </code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">getCommissionRate() * getGrossSales();                    </code>

<code class="php spaces">   </code><code class="php plain">}                                             </code>

<code class="php spaces">   </code><code class="php comments">// return String representation of CommissionEmployee object</code>

<code class="php spaces">   </code><code class="php plain">@Override                                                   </code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">String toString()                                    </code>

<code class="php spaces">   </code><code class="php plain">{                                                           </code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">String.format(</code><code class="php string">"%s: %s%n%s: $%,.2f; %s: %.2f"</code><code class="php plain">,    </code>

<code class="php spaces">         </code><code class="php string">"commission employee"</code><code class="php plain">, super.toString(),              </code>

<code class="php spaces">         </code><code class="php string">"gross sales"</code><code class="php plain">, getGrossSales(),                       </code>

<code class="php spaces">         </code><code class="php string">"commission rate"</code><code class="php plain">, getCommissionRate());             </code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php plain">} </code><code class="php comments">// end class CommissionEmployee</code>

<code class="php comments">// Fig. 10.8: BasePlusCommissionEmployee.java</code>

<code class="php comments">// BasePlusCommissionEmployee class extends CommissionEmployee.</code>

<code class="php keyword">public</code> <code class="php keyword">class</code> <code class="php plain">BasePlusCommissionEmployee </code><code class="php keyword">extends</code> <code class="php plain">CommissionEmployee </code>

<code class="php plain">{</code>

<code class="php spaces">   </code><code class="php keyword">private</code> <code class="php plain">double baseSalary; </code><code class="php comments">// base salary per week</code>

<code class="php spaces">   </code><code class="php comments">// constructor</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">BasePlusCommissionEmployee(String firstName, String lastName, </code>

<code class="php spaces">      </code><code class="php plain">String socialSecurityNumber, double grossSales,</code>

<code class="php spaces">      </code><code class="php plain">double commissionRate, double baseSalary)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php plain">super(firstName, lastName, socialSecurityNumber, </code>

<code class="php spaces">         </code><code class="php plain">grossSales, commissionRate);</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(baseSalary &lt; 0.0) </code><code class="php comments">// validate baseSalary                  </code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code><code class="php string">"Base salary must be &gt;= 0.0"</code><code class="php plain">);</code>

<code class="php spaces">            </code>

<code class="php spaces">      </code><code class="php plain">this.baseSalary = baseSalary;                </code>

<code class="php spaces">   </code><code class="php plain">}</code>

<code class="php spaces">   </code><code class="php comments">// set base salary</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">void setBaseSalary(double baseSalary)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(baseSalary &lt; 0.0) </code><code class="php comments">// validate baseSalary                  </code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code><code class="php string">"Base salary must be &gt;= 0.0"</code><code class="php plain">);</code>

<code class="php spaces">            </code>

<code class="php spaces">      </code><code class="php plain">this.baseSalary = baseSalary;                </code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return base salary</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">double getBaseSalary()</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">baseSalary;</code>

<code class="php spaces">   </code><code class="php plain">}</code>

<code class="php spaces">   </code><code class="php comments">// calculate earnings; override method earnings in CommissionEmployee</code>

<code class="php spaces">   </code><code class="php plain">@Override                                                            </code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">double earnings()                                             </code>

<code class="php spaces">   </code><code class="php plain">{                                                                    </code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">getBaseSalary() + super.earnings();                        </code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return String representation of BasePlusCommissionEmployee object</code>

<code class="php spaces">   </code><code class="php plain">@Override                                                           </code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">String toString()                                            </code>

<code class="php spaces">   </code><code class="php plain">{                                                                   </code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">String.format(</code><code class="php string">"%s %s; %s: $%,.2f"</code><code class="php plain">,                       </code>

<code class="php spaces">         </code><code class="php string">"base-salaried"</code><code class="php plain">, super.toString(),                            </code>

<code class="php spaces">         </code><code class="php string">"base salary"</code><code class="php plain">, getBaseSalary());                             </code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php plain">} </code><code class="php comments">// end class BasePlusCommissionEmployee</code>

<code class="php comments">// Fig. 10.4: Employee.java</code>

<code class="php comments">// Employee abstract superclass.</code>

<code class="php keyword">public</code> <code class="php keyword">abstract</code> <code class="php keyword">class</code> <code class="php plain">Employee </code>

<code class="php plain">{</code>

<code class="php spaces">   </code><code class="php keyword">private</code> <code class="php keyword">final</code> <code class="php plain">String firstName;</code>

<code class="php spaces">   </code><code class="php keyword">private</code> <code class="php keyword">final</code> <code class="php plain">String lastName;</code>

<code class="php spaces">   </code><code class="php keyword">private</code> <code class="php keyword">final</code> <code class="php plain">String socialSecurityNumber;</code>

<code class="php spaces">   </code><code class="php comments">// constructor</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">Employee(String firstName, String lastName, </code>

<code class="php spaces">      </code><code class="php plain">String socialSecurityNumber)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php plain">this.firstName = firstName;                                    </code>

<code class="php spaces">      </code><code class="php plain">this.lastName = lastName;                                    </code>

<code class="php spaces">      </code><code class="php plain">this.socialSecurityNumber = socialSecurityNumber;         </code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return first name</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">String getFirstName()</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">firstName;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return last name</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">String getLastName()</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">lastName;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return social security number</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">String getSocialSecurityNumber()</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">socialSecurityNumber;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return String representation of Employee object</code>

<code class="php spaces">   </code><code class="php plain">@Override</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">String toString()</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">String.format(</code><code class="php string">"%s %s%nsocial security number: %s"</code><code class="php plain">, </code>

<code class="php spaces">         </code><code class="php plain">getFirstName(), getLastName(), getSocialSecurityNumber());</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// abstract method must be overridden by concrete subclasses</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php keyword">abstract</code> <code class="php plain">double earnings(); </code><code class="php comments">// no implementation here</code>

<code class="php plain">} </code><code class="php comments">// end abstract class Employee</code>

<code class="php comments">// Fig. 10.6: HourlyEmployee.java</code>

<code class="php comments">// HourlyEmployee class extends Employee.</code>

<code class="php keyword">public</code> <code class="php keyword">class</code> <code class="php plain">HourlyEmployee </code><code class="php keyword">extends</code> <code class="php plain">Employee </code>

<code class="php plain">{</code>

<code class="php spaces">   </code><code class="php keyword">private</code> <code class="php plain">double wage; </code><code class="php comments">// wage per hour</code>

<code class="php spaces">   </code><code class="php keyword">private</code> <code class="php plain">double hours; </code><code class="php comments">// hours worked for week</code>

<code class="php spaces">   </code><code class="php comments">// constructor</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">HourlyEmployee(String firstName, String lastName,</code>

<code class="php spaces">      </code><code class="php plain">String socialSecurityNumber, double wage, double hours)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php plain">super(firstName, lastName, socialSecurityNumber);</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(wage &lt; 0.0) </code><code class="php comments">// validate wage</code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code>

<code class="php spaces">            </code><code class="php string">"Hourly wage must be &gt;= 0.0"</code><code class="php plain">);</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">((hours &lt; 0.0) || (hours &gt; 168.0)) </code><code class="php comments">// validate hours</code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code>

<code class="php spaces">            </code><code class="php string">"Hours worked must be &gt;= 0.0 and &lt;= 168.0"</code><code class="php plain">);</code>

<code class="php spaces">      </code><code class="php plain">this.wage = wage;</code>

<code class="php spaces">      </code><code class="php plain">this.hours = hours;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// set wage</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">void setWage(double wage)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(wage &lt; 0.0) </code><code class="php comments">// validate wage</code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code>

<code class="php spaces">            </code><code class="php string">"Hourly wage must be &gt;= 0.0"</code><code class="php plain">);</code>

<code class="php spaces">      </code><code class="php plain">this.wage = wage;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return wage</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">double getWage()</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">wage;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// set hours worked</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">void setHours(double hours)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">((hours &lt; 0.0) || (hours &gt; 168.0)) </code><code class="php comments">// validate hours</code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code>

<code class="php spaces">            </code><code class="php string">"Hours worked must be &gt;= 0.0 and &lt;= 168.0"</code><code class="php plain">);</code>

<code class="php spaces">      </code><code class="php plain">this.hours = hours;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return hours worked</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">double getHours()</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">hours;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// calculate earnings; override abstract method earnings in Employee</code>

<code class="php spaces">   </code><code class="php plain">@Override                                                           </code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">double earnings()                                            </code>

<code class="php spaces">   </code><code class="php plain">{                                                                   </code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(getHours() &lt;= 40) </code><code class="php comments">// no overtime                           </code>

<code class="php spaces">         </code><code class="php keyword">return</code> <code class="php plain">getWage() * getHours();                                </code>

<code class="php spaces">      </code><code class="php keyword">else</code>

<code class="php spaces">         </code><code class="php keyword">return</code> <code class="php plain">40 * getWage() + (getHours() - 40) * getWage() * 1.5;</code>

<code class="php spaces">   </code><code class="php plain">}                                          </code>

<code class="php spaces">   </code><code class="php comments">// return String representation of HourlyEmployee object              </code>

<code class="php spaces">   </code><code class="php plain">@Override                                                             </code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">String toString()                                              </code>

<code class="php spaces">   </code><code class="php plain">{                                                                     </code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">String.format(</code><code class="php string">"hourly employee: %s%n%s: $%,.2f; %s: %,.2f"</code><code class="php plain">,</code>

<code class="php spaces">         </code><code class="php plain">super.toString(), </code><code class="php string">"hourly wage"</code><code class="php plain">, getWage(),                     </code>

<code class="php spaces">         </code><code class="php string">"hours worked"</code><code class="php plain">, getHours());                                   </code>

<code class="php spaces">   </code><code class="php plain">}                                    </code>

<code class="php plain">} </code><code class="php comments">// end class HourlyEmployee</code>

<code class="php comments">// Fig. 10.9: PayrollSystemTest.java</code>

<code class="php comments">// Employee hierarchy test program.</code>

<code class="php keyword">public</code> <code class="php keyword">class</code> <code class="php plain">PayrollSystemTest </code>

<code class="php plain">{</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php keyword">static</code> <code class="php plain">void main(String[] args) </code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php comments">// create subclass objects</code>

<code class="php spaces">      </code><code class="php plain">SalariedEmployee salariedEmployee = </code>

<code class="php spaces">         </code><code class="php keyword">new</code> <code class="php plain">SalariedEmployee(</code><code class="php string">"John"</code><code class="php plain">, </code><code class="php string">"Smith"</code><code class="php plain">, </code><code class="php string">"111-11-1111"</code><code class="php plain">, 800.00);</code>

<code class="php spaces">      </code><code class="php plain">HourlyEmployee hourlyEmployee = </code>

<code class="php spaces">         </code><code class="php keyword">new</code> <code class="php plain">HourlyEmployee(</code><code class="php string">"Karen"</code><code class="php plain">, </code><code class="php string">"Price"</code><code class="php plain">, </code><code class="php string">"222-22-2222"</code><code class="php plain">, 16.75, 40);</code>

<code class="php spaces">      </code><code class="php plain">CommissionEmployee commissionEmployee = </code>

<code class="php spaces">         </code><code class="php keyword">new</code> <code class="php plain">CommissionEmployee(</code>

<code class="php spaces">         </code><code class="php string">"Sue"</code><code class="php plain">, </code><code class="php string">"Jones"</code><code class="php plain">, </code><code class="php string">"333-33-3333"</code><code class="php plain">, 10000, .06);</code>

<code class="php spaces">      </code><code class="php plain">BasePlusCommissionEmployee basePlusCommissionEmployee = </code>

<code class="php spaces">         </code><code class="php keyword">new</code> <code class="php plain">BasePlusCommissionEmployee(</code>

<code class="php spaces">         </code><code class="php string">"Bob"</code><code class="php plain">, </code><code class="php string">"Lewis"</code><code class="php plain">, </code><code class="php string">"444-44-4444"</code><code class="php plain">, 5000, .04, 300);</code>

<code class="php spaces">      </code><code class="php plain">System.out.println(</code><code class="php string">"Employees processed individually:"</code><code class="php plain">);</code>

<code class="php spaces">      </code>

<code class="php spaces">      </code><code class="php plain">System.out.printf(</code><code class="php string">"%n%s%n%s: $%,.2f%n%n"</code><code class="php plain">, </code>

<code class="php spaces">         </code><code class="php plain">salariedEmployee, </code><code class="php string">"earned"</code><code class="php plain">, salariedEmployee.earnings());</code>

<code class="php spaces">      </code><code class="php plain">System.out.printf(</code><code class="php string">"%s%n%s: $%,.2f%n%n"</code><code class="php plain">,</code>

<code class="php spaces">         </code><code class="php plain">hourlyEmployee, </code><code class="php string">"earned"</code><code class="php plain">, hourlyEmployee.earnings());</code>

<code class="php spaces">      </code><code class="php plain">System.out.printf(</code><code class="php string">"%s%n%s: $%,.2f%n%n"</code><code class="php plain">,</code>

<code class="php spaces">         </code><code class="php plain">commissionEmployee, </code><code class="php string">"earned"</code><code class="php plain">, commissionEmployee.earnings());</code>

<code class="php spaces">      </code><code class="php plain">System.out.printf(</code><code class="php string">"%s%n%s: $%,.2f%n%n"</code><code class="php plain">, </code>

<code class="php spaces">         </code><code class="php plain">basePlusCommissionEmployee, </code>

<code class="php spaces">         </code><code class="php string">"earned"</code><code class="php plain">, basePlusCommissionEmployee.earnings());</code>

<code class="php spaces">      </code><code class="php comments">// create four-element Employee array</code>

<code class="php spaces">      </code><code class="php plain">Employee[] employees = </code><code class="php keyword">new</code> <code class="php plain">Employee[4]; </code>

<code class="php spaces">      </code><code class="php comments">// initialize array with Employees</code>

<code class="php spaces">      </code><code class="php plain">employees[0] = salariedEmployee;</code>

<code class="php spaces">      </code><code class="php plain">employees[1] = hourlyEmployee;</code>

<code class="php spaces">      </code><code class="php plain">employees[2] = commissionEmployee; </code>

<code class="php spaces">      </code><code class="php plain">employees[3] = basePlusCommissionEmployee;</code>

<code class="php spaces">      </code><code class="php plain">System.out.printf(</code><code class="php string">"Employees processed polymorphically:%n%n"</code><code class="php plain">);</code>

<code class="php spaces">      </code>

<code class="php spaces">      </code><code class="php comments">// generically process each element in array employees</code>

<code class="php spaces">      </code><code class="php keyword">for</code> <code class="php plain">(Employee currentEmployee : employees) </code>

<code class="php spaces">      </code><code class="php plain">{</code>

<code class="php spaces">         </code><code class="php plain">System.out.println(currentEmployee); </code><code class="php comments">// invokes toString</code>

<code class="php spaces">         </code><code class="php comments">// determine whether element is a BasePlusCommissionEmployee</code>

<code class="php spaces">         </code><code class="php keyword">if</code> <code class="php plain">(currentEmployee </code><code class="php keyword">instanceof</code> <code class="php plain">BasePlusCommissionEmployee) </code>

<code class="php spaces">         </code><code class="php plain">{</code>

<code class="php spaces">            </code><code class="php comments">// downcast Employee reference to </code>

<code class="php spaces">            </code><code class="php comments">// BasePlusCommissionEmployee reference</code>

<code class="php spaces">            </code><code class="php plain">BasePlusCommissionEmployee employee = </code>

<code class="php spaces">               </code><code class="php plain">(BasePlusCommissionEmployee) currentEmployee;</code>

<code class="php spaces">            </code><code class="php plain">employee.setBaseSalary(1.10 * employee.getBaseSalary());</code>

<code class="php spaces">            </code><code class="php plain">System.out.printf(</code>

<code class="php spaces">               </code><code class="php string">"new base salary with 10%% increase is: $%,.2f%n"</code><code class="php plain">,</code>

<code class="php spaces">               </code><code class="php plain">employee.getBaseSalary());</code>

<code class="php spaces">         </code><code class="php plain">} </code>

<code class="php spaces">         </code><code class="php plain">System.out.printf(</code>

<code class="php spaces">            </code><code class="php string">"earned $%,.2f%n%n"</code><code class="php plain">, currentEmployee.earnings());</code>

<code class="php spaces">      </code><code class="php plain">} </code>

<code class="php spaces">      </code><code class="php comments">// get type name of each object in employees array</code>

<code class="php spaces">      </code><code class="php keyword">for</code> <code class="php plain">(int j = 0; j &lt; employees.length; j++)</code>

<code class="php spaces">         </code><code class="php plain">System.out.printf(</code><code class="php string">"Employee %d is a %s%n"</code><code class="php plain">, j, </code>

<code class="php spaces">            </code><code class="php plain">employees[j].getClass().getName()); </code>

<code class="php spaces">   </code><code class="php plain">} </code><code class="php comments">// end main</code>

<code class="php plain">} </code><code class="php comments">// end class PayrollSystemTest</code>

<code class="php comments">// Fig. 10.5: SalariedEmployee.java</code>

<code class="php comments">// SalariedEmployee concrete class extends abstract class Employee.</code>

<code class="php keyword">public</code> <code class="php keyword">class</code> <code class="php plain">SalariedEmployee </code><code class="php keyword">extends</code> <code class="php plain">Employee </code>

<code class="php plain">{</code>

<code class="php spaces">   </code><code class="php keyword">private</code> <code class="php plain">double weeklySalary;</code>

<code class="php spaces">   </code><code class="php comments">// constructor</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">SalariedEmployee(String firstName, String lastName, </code>

<code class="php spaces">      </code><code class="php plain">String socialSecurityNumber, double weeklySalary)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php plain">super(firstName, lastName, socialSecurityNumber); </code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(weeklySalary &lt; 0.0)</code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code>

<code class="php spaces">            </code><code class="php string">"Weekly salary must be &gt;= 0.0"</code><code class="php plain">);</code>

<code class="php spaces">      </code><code class="php plain">this.weeklySalary = weeklySalary;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// set salary</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">void setWeeklySalary(double weeklySalary)</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">if</code> <code class="php plain">(weeklySalary &lt; 0.0)</code>

<code class="php spaces">         </code><code class="php keyword">throw</code> <code class="php keyword">new</code> <code class="php plain">IllegalArgumentException(</code>

<code class="php spaces">            </code><code class="php string">"Weekly salary must be &gt;= 0.0"</code><code class="php plain">);</code>

<code class="php spaces">      </code><code class="php plain">this.weeklySalary = weeklySalary;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// return salary</code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">double getWeeklySalary()</code>

<code class="php spaces">   </code><code class="php plain">{</code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">weeklySalary;</code>

<code class="php spaces">   </code><code class="php plain">} </code>

<code class="php spaces">   </code><code class="php comments">// calculate earnings; override abstract method earnings in Employee</code>

<code class="php spaces">   </code><code class="php plain">@Override                                                           </code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">double earnings()                                            </code>

<code class="php spaces">   </code><code class="php plain">{                                                                   </code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">getWeeklySalary();                                        </code>

<code class="php spaces">   </code><code class="php plain">}                                             </code>

<code class="php spaces">   </code><code class="php comments">// return String representation of SalariedEmployee object   </code>

<code class="php spaces">   </code><code class="php plain">@Override                                                    </code>

<code class="php spaces">   </code><code class="php keyword">public</code> <code class="php plain">String toString()                                     </code>

<code class="php spaces">   </code><code class="php plain">{                                                            </code>

<code class="php spaces">      </code><code class="php keyword">return</code> <code class="php plain">String.format(</code><code class="php string">"salaried employee: %s%n%s: $%,.2f"</code><code class="php plain">,</code>

<code class="php spaces">         </code><code class="php plain">super.toString(), </code><code class="php string">"weekly salary"</code><code class="php plain">, getWeeklySalary());</code>

<code class="php spaces">   </code><code class="php plain">} </code>